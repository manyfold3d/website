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

`HTTPS_ONLY=enabled`

## File uploads

`MAX_FILE_UPLOAD_SIZE` - 256MiB by default
`MAX_FILE_EXTRACT_SIZE` - 1GiB by default

## Container permissions

`--security-opts no-new-privileges:true`
`--cap-drop=ALL`
`--cap-add=CHOWN,SETUID,SETGID`
`--read-only=true`
