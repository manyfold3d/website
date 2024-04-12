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

Alternatively, you can set server, username, password and name separately; see the [Database](#database) section.

### `REDIS_URL`

A string that includes all the information necessary to connect to a Redis server, in the form `redis://{redis_server}:{port}/{dbnumber}`; for instance `redis://redis:6379/1`.

### `SECRET_KEY_BASE`

A secret key used to sign browser cookies; normally a 128-digit hexadecimal number, but any long random string will do. If you have the code checked out, you can generate one with `rake secret`. Changing this will invalidate all user cookies and sessions.

## Features

### `DEMO_MODE`
<small>Version 0.55.0+</small>

Set to `enabled` to put the entire site into the demo mode used on [try.manyfold.app](https://try.manyfold.app). In this mode, all deletion, upload, and advanced admin features are disabled, even in single-user mode and for administrator users. You're pretty unlikely to need it, though perhaps you could use it as a sort of "emergency lockdown" mode.

### `REGISTRATION`
<small>Version 0.59.0+</small>

If `MULTIUSER` is enabled, set to `enabled` to allow new users to sign up for account. If disabled, users will need to be invited by an admin. Off by default.

### `MULTIUSER`
<small>Version 0.59.0+</small>

Set to `enabled` to turn on multiuser features such as account login, signup (with `REGISTRATION` option), permissions, roles, and so on. By default this is off, and Manyfold operates in single-user mode without any login necessary; however, if you're exposing your Manyfold instance on the public Internet, even if you intend to only use it yourself, it's probably a good idea to enable multiuser for security.

{:.important}
You should set a secure administrator password before turning on multiuser mode. Manyfold should prompt you to do so when you first access version 0.59.0 or above.

## Network

### `RAILS_RELATIVE_URL_ROOT`

If you are mapping Manyfold to a non-root path via a reverse proxy like nginx, use this option to tell Manyfold what the root path is; for instance `/manyfold`.

## Database

Instead of setting `DATABASE_URL` as above, you can set separate variables for each component. If you do this, all variables in this section are required.

### `DATABASE_HOST`
<small>Version 0.60.0+</small>

The hostname of your PostgreSQL server.

### `DATABASE_USER`
<small>Version 0.60.0+</small>

The username used to authenticate to PostgreSQL.

### `DATABASE_PASSWORD`
<small>Version 0.60.0+</small>

The password used to authenticate to PostgreSQL.

### `DATABASE_NAME`
<small>Version 0.60.0+</small>

Your PostgreSQL database name.

## Email

Some multiuser features are only enabled if an email server is configured, such as password recovery, email verification, and so on.

In order to send mail, you need an SMTP server to send through; this could be your own local mail server, your own email host like gmail, or a hosted SMTP service like [Mandrill](https://www.mandrillapp.com/).

### `SMTP_SERVER`
<small>Version 0.61.0+</small>

The hostname of your SMTP server, e.g. `smtp.example.com`. The default port 25 will be used.

If the server supports TLS, it will be used automatically with `STARTTLS`, but otherwise an unencrypted connection will be used. See [ActionMailer's SMTP documentation](https://guides.rubyonrails.org/action_mailer_basics.html#action-mailer-configuration) for details. Defaults to `localhost`.

### `SMTP_USERNAME`
<small>Version 0.61.0+</small>

The username for your mail server, if authentication is required.

### `SMTP_PASSWORD`
<small>Version 0.61.0+</small>

The password for your mail server, if authentication is required.

### `SMTP_FROM_ADDRESS`
<small>Version 0.61.0+</small>

The email address that mails should appear to be sent from. If not set, mail is sent from `notifications@{PUBLIC_HOSTNAME}`.

### `PUBLIC_HOSTNAME`
<small>Version 0.61.0+</small>

The hostname of your publicly-accessible service, e.g. `try.manyfold.app`. This variable is used to create links in emails, and _must_ be set for email delivery to work.

### `PUBLIC_PORT`
<small>Version 0.61.0+</small>

If your public service is on a non-standard port, set it here (e.g. `3214`).
