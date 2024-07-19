---
title: Security
parent: Admin Guide
layout: page
nav_order: 3
---

This page describes how to configure your Manyfold instance to run securely. Some things are built-in options, and some are changes to your Docker configuration that you'll need to apply yourself.

## `PUID` and `PGID`

By default, Docker containers run as root. This is a security concern, especially for an application that manipulates files on disk!

In order to increase security, and so that all the created files aren't owned by root, Manyfold should be run as a less-privileged user. In line with the [Linuxserver approach](https://docs.linuxserver.io/general/understanding-puid-and-pgid/), this is done by setting the user and group ID to run as using the `PUID` and `PGID` environment variables.

 `docker create -e PUID=1000 -e PGID=1000 ghcr.io/manyfold3d/manyfold:latest`

If these are set, the container will start and set up as root, but then drop to this less privileged user when actually running the app.

If not set, the application will run as root, but will continuously warn admins to fix it, and will fail to start in a future release, probably v1.0.0.

To get your user and group IDs, run `id` and look at the `uid` and `gid` values.

{:.note}
Make sure that your libraries and files are readable and writable by the user you run as!

{:.important}
Manyfold does not currently support Docker's built-in `user` option; if you set that, it will drop privileges too early. Hopefully we can make it work in a future release.

## Enforcing secure connections

If you're running an instance anywhere except your own private network, it should be using HTTPS. Manyfold itself doesn't (yet) provide SSL termination, but if you're [running behind a proxy](proxies.md), you can put the app into secure-only mode using the following environment variable:

`HTTPS_ONLY=enabled`

This will do three things:

1. Automatically redirects any HTTP requests to HTTPS. The proxy is probably already doing this, but just in case, the application will as well. Make sure your proxy is setting `X-Forwarded-Proto` appropriately so you don't get infinite loops!
2. Set the `Strict-Transport-Security` header (aka [HSTS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security)).
3. Set all cookies to `secure`, meaning they will only be sent over HTTPS connections.

{:.important}
The HSTS header has a long expiry time, so this is effectively a one-way switch! By turning it on you will lose unencrypted access to your instance for a long time, so make sure HTTPS is working first!


## File uploads

An attacker with upload capability could upload a file that's too big for your server, or even a [zip bomb](https://en.wikipedia.org/wiki/Zip_bomb) in order to cause problems. To avoid that, there are two environment variables to control uploads:

* `MAX_FILE_UPLOAD_SIZE`: sets the maximum size of any individual uploaded file. 256MiB by default.
* `MAX_FILE_EXTRACT_SIZE`: sets the maximum size of any extracted file. 1GiB by default.

To change these sizes, set a number _in bytes_ in the environment variable. For instance, to allow up to 512MiB uploads, set `MAX_FILE_UPLOAD_SIZE=536870912`.

## Container permissions

You should always make sure that you're running Docker containers securely. After all, can you *really* trust a downloaded image without going through every line of code? This is a very [big topic](https://docs.docker.com/engine/security/) that we can't explain fully here, but we can recommend some basic security options that you can set on the command line or in your compose file.

### Privileges

The container runs as root, and then drops to a different user once initialized, as described about in the `PUID` documentation. To minimise what the container can do as much as possible, you can set some privilege options.

First, you should forbid privilege escalation, using the `no-new-privileges` security option.

Then, you can set the container's capabilities by dropping all default capabilities, then adding back only the ones Manyfold really needs. Manyfold uses `CHOWN` and `DAC_OVERRIDE` permissions to make sure temp and log files are writable by the `PUID` user, then uses `SETUID` and `SETGID` to actually change to that user. No others are required.

On the docker command line, you can set these options using the following arguments:

`--security-opt=no-new-privileges:true --cap-drop=ALL --cap-add=CHOWN,DAC_OVERRIDE,SETUID,SETGID`

Or, if you're using docker-compose:

```yaml
security_opt:
  - no-new-privileges:true
cap_drop:
  - ALL
cap_add:
  - CHOWN
  - DAC_OVERRIDE
  - SETUID
  - SETGID
```

### Read-only filesystem

By setting `read-only` on your container, you can prevent the application from writing to the image filesystem, thus preventing attackers from (for instance) changing the running code.

On the docker command line:

`--read-only`

In docker-compose:

```yaml
read_only: true
```

{:.important}
If you set this option, you will need to map some extra volumes, because Manyfold does need to write to some temporary files.

The required paths are:

* `/tmp`
* `/usr/src/app/tmp`
* `/usr/src/app/log`
* `/run`

You might map these to a specific place on your host (apart from `/run` which should be a `tmpfs` mount). In docker-compose:

```yaml
tmpfs:
  - /run:exec
volumes:
  - /var/manyfold/sys_tmp:/tmp
  - /var/manyfold/app_tmp:/usr/src/app/tmp
  - /var/manyfold/log:/usr/src/app/log
```
