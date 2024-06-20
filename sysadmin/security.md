---
title: Security
parent: Running Manyfold
layout: page
nav_order: 3
---

## PUID and PGID

`PUID` and `PGID`

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
