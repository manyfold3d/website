---
title: Security
parent: Running Manyfold
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

`--security-opts no-new-privileges:true`
`--cap-drop=ALL`
`--cap-add=CHOWN,SETUID,SETGID`
`--read-only=true`
