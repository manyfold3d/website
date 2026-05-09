---
title: Proxies
parent: Admin Guide
layout: page
nav_order: 6
---

You may want to run Manyfold behind a reverse proxy, in order to provide HTTPS termination, or run it on a path. This page lists some considerations you'll need to take into account.

## Paths

If you want to run Manyfold on a non-root path, for instance at `https://example.com/manyfold`, you should set the path in the `RAILS_RELATIVE_URL_ROOT` Docker environment variable.

```
RAILS_RELATIVE_URL_ROOT: /manyfold
```

## SSL Termination

In order for Manyfold to correctly realise it's running behind an HTTPS proxy, you'll need to make sure a few extra HTTP headers are set between the proxy and the app. If you don't, you'll get CORS origin errors. The snippet below shows the settings for HAProxy; your preferred proxy will have similar options:

```
http-request set-header X-Forwarded-Ssl on
http-request set-header X-Forwarded-Proto https
http-request set-header X-Forwarded-Port 443
http-request set-header X-Forwarded-Host "YOUR_DOMAIN"
```

## Sample proxy configurations

### Nginx (by [vmario89](https://github.com/manyfold3d/manyfold/issues/4203#issuecomment-4409829534))

```nginx
server {
    server_name manyfold.some.host;
    ssl_certificate /etc/letsencrypt/live/some.host/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/some.host/privkey.pem;
    ssl_session_timeout 5m;
    ssl_session_cache   shared:SSL:10m;
    ssl_session_tickets off;
    ssl_prefer_server_ciphers off;
    ssl_ecdh_curve X25519:prime256v1:secp384r1;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-CHACHA20-POLY1305;
    ssl_dhparam "/etc/nginx/dhparam";

    listen 443 ssl;
    listen [::]:443 ssl;
    http2 on;

    quic_retry on;
    ssl_early_data on;
    quic_gso on;
    listen 443 quic;
    listen [::]:443 quic;
    http3 on;
    http3_hq on;
    add_header Alt-Svc 'h3=":$server_port"; ma=86400';
    add_header Alt-Svc 'h3-29=":$server_port"; ma=86400';
    add_header x-quic 'h3';

    error_log /var/log/nginx/$host.error.log;

    #add_header X-Frame-Options SAMEORIGIN always;
    add_header X-Xss-Protection "1; mode=block" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header Referrer-Policy same-origin always;
    add_header Content-Security-Policy "default-src * 'unsafe-inline' 'unsafe-eval' data: blob:; img-src: 'self' blob: https://some.host; style-src: 'self' 'unsafe-inline';" always;
    add_header Strict-Transport-Security "max-age=63072000; includeSubDomains; preload" always;
    add_header Permissions-Policy "geolocation 'none'; camera 'none'; speaker 'none';";

    client_max_body_size 500M;

    location / {
        proxy_pass http://127.0.0.1:3214;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        tcp_nodelay on;
    }

    location /cable {
        proxy_pass http://127.0.0.1:3214;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection $connection_upgrade;
        proxy_http_version 1.1;
    }

    location = /.well-known/security.txt {
        return 301 https://some.host/.well-known/security.txt;
    }
}

server {
    listen 80;
    listen [::]:80;
    server_name manyfold.some.host;
    location / {
        return 301 https://$host$request_uri;
    }
}
```
