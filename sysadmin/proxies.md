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
