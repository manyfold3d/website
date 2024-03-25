---
title: Configuration
parent: Running Manyfold
layout: page
nav_order: 1
---

Most global configuration for Manyfold is via environment variables. These could be set in your docker configuration as shown in [Get Started](/get-started/docker-compose.html), in a `.env` file for local development, or in some other way that makes sense for your deployment setup.

This page lists the available environment variables, and describes the effect of each one.

## Required

{:.important}
The variables in this section **must** be set, or the application will not start.

### `DATABASE_URL`

A string that includes all the information necessary to connect to a PostgreSQL database, in the form `postgresql://{username}:{password}@{database_server}/{database_name}?pool=5`. For a complete description, and more options, see the [PostgreSQL connection string documentation](https://www.postgresql.org/docs/current/libpq-connect.html#LIBPQ-CONNSTRING-URIS).

### `REDIS_URL`

A string that includes all the information necessary to connect to a Redis server, in the form `redis://{redis_server}:{port}/{dbnumber}`; for instance `redis://redis:6379/1`.

### `SECRET_KEY_BASE`

A secret key used to sign browser cookies; normally a 128-digit hexadecimal number, but any long random string will do. If you have the code checked out, you can generate one with `rake secret`. Changing this will invalidate all user cookies and sessions.

## Features

### `DEMO_MODE`

Set to `enabled` to put the entire site into the demo mode used on [try.manyfold.app](https://try.manyfold.app). In this mode, all deletion, upload, and advanced admin features are disabled, even in single-user mode and for administrator users. You're pretty unlikely to need it, though perhaps you could use it as a sort of "emergency lockdown" mode.

### `REGISTRATION`

If `MULTIUSER` is enabled, set to `enabled` to allow new users to sign up for account. If disabled, users will need to be invited by an admin. Off by default.

### `MULTIUSER`

Set to `enabled` to turn on multiuser features such as account login, signup (with `REGISTRATION` option), permissions, roles, and so on. By default this is off, and Manyfold operates in single-user mode without any login necessary; however, if you're exposing your Manyfold instance on the public Internet, even if you intend to only use it yourself, it's probably a good idea to enable multiuser for security.

{:.important}
You should set a secure administrator password before turning on multiuser mode. Manyfold should prompt you to do so when you first access version 0.59.0 or above.

## Network

### `RAILS_RELATIVE_URL_ROOT`

If you are mapping Manyfold to a non-root path via a reverse proxy like nginx, use this option to tell Manyfold what the root path is; for instance `/manyfold`.
