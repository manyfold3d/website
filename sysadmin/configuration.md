---
title: Configuration
parent: Admin Guide
layout: page
nav_order: 1
---

Most global configuration for Manyfold is via environment variables. These could be set in your docker configuration as shown in [Get Started](/get-started/docker-compose.html), in a `.env` file for local development, or in some other way that makes sense for your deployment setup.

This page lists the available environment variables, and describes the effect of each one.

## Required

{:.important}
The variables in this section **must** be set, or the application will not start.

### `PUID` and `PGID`
<small>Version 0.69.0+</small>

Set the user and group IDs that the Manyfold application should run as. Works the same as it does in [Linuxserver containers](https://docs.linuxserver.io/general/understanding-puid-and-pgid/).

For example: `PUID=1000` and `PGID=1000`

To get your user and group IDs, run `id` and look at the `uid` and `gid` values. Read our [security guide](security) for more details.

### `SECRET_KEY_BASE`

A secret key used to sign browser cookies; normally a 128-digit hexadecimal number, but any long random string will do. If you have the code checked out, you can generate one with `bundle exec rails secret`. Changing this will invalidate all user cookies and sessions.

### `REDIS_URL`
<small>`manyfold` image only, not required for `manyfold-solo`</small>

A string that includes all the information necessary to connect to a Redis server, in the form `redis://{redis_server}:{port}/{dbnumber}`; for instance `redis://redis:6379/1`.

## Database

If you're using the `manyfold` image, you need to provide *either* a `DATABASE_URL` or a set of separate `DATABASE_*` parameters. If you're using `manyfold-solo`, as long as you have mounted persistent storage at `/config`, you do not need any more database configuration.

### `DATABASE_ADAPTER`
<small>Version 0.72.0+</small>

Specifies the type of database being connected to. Supported values are:

|DATABASE_ADAPTER|Server|Default?|
|--|--|--|
|`postgresql`|[PostgreSQL](https://postgresql.org)|yes|
|`mysql2`|[MySQL](https://www.mysql.com/) or [MariaDB](https://mariadb.org/)||
|`sqlite3`|[SQLite](https://www.sqlite.org)||

### `DATABASE_HOST`
<small>Version 0.60.0+</small>

The hostname of your database server. Not required for `sqlite3`.

### `DATABASE_USER`
<small>Version 0.60.0+</small>

The username used to authenticate to your database server. Not required for `sqlite3`.

### `DATABASE_PASSWORD`
<small>Version 0.60.0+</small>

The password used to authenticate to your database server. Not required for `sqlite3`.

### `DATABASE_NAME`
<small>Version 0.60.0+</small>

For `postgresql` and `mysql2`, this should be the name of the database you want to use. For `sqlite3`, this
should specify the absolute path of the database file, e.g. `/config/manyfold.sqlite3`

### `DATABASE_CONNECTION_POOL`
<small>Version 0.70.0+</small>

Specifies the number of database connections to share across the application. Defaults to `RAILS_MAX_THREADS` or `16`, which should be fine in most cases.

### `DATABASE_URL`

A single string that combines all the information necessary to connect to your database. This will override any other information specified in the other `DATABASE_*` variables. The exact format varies slightly depending on the database adapter you want to use:

* [PostgreSQL](https://www.postgresql.org/docs/current/libpq-connect.html#LIBPQ-CONNSTRING-URIS): `postgresql://{username}:{password}@{database_server}/{database_name}?pool={pool_size}`
* [MySQL/MariaDB](https://dev.mysql.com/doc/refman/8.0/en/connecting-using-uri-or-key-value-pairs.html): `mysql2://{username}:{password}@{database_server}/{database_name}?pool={pool_size}`
* [SQLite](https://www.sqlite.org/c3ref/open.html#urifilenamesinsqlite3open): `sqlite3:{absolute_path_of_database_file}?pool={pool_size}`

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

### `HTTPS_ONLY`
<small>Version 0.69.0+</small>

Put the application into HTTPS-only mode, including automatic HTTPS redirection, Strict-Transport-Security, and secure cookies. Read the [security](security) page for important details.

{:.important}
The HSTS header has a long expiry time, so this is effectively a one-way switch! By turning it on you will lose unencrypted access to your instance for a long time, so make sure HTTPS is working first!

### `RAILS_RELATIVE_URL_ROOT`

If you are mapping Manyfold to a non-root path via a reverse proxy like nginx, use this option to tell Manyfold what the root path is; for instance `/manyfold`.

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

## Performance

### `WEB_CONCURRENCY`

Sets the number of web workers run by the application. Recommended to be the same or slightly less than the number of available CPU cores for best performance. Defaults to 4. The number of concurrent requests that can be served is `WEB_CONCURRENCY` * `RAILS_MAX_THREADS`.

### `RAILS_MAX_THREADS`

The maximum number of threads that each worker should run. Each thread can serve one request at a time, so the number of concurrent requests that can be served is `WEB_CONCURRENCY` * `RAILS_MAX_THREADS`. Defaults to 16.

### `DEFAULT_WORKER_CONCURRENCY`
<small>Version 0.70.0+</small>

The number of standard worker threads to run. If you have more CPU power and memory, you may want to increase this to get faster
job processing. 4 by default.

### `PERFORMANCE_WORKER_CONCURRENCY`
<small>Version 0.70.0+</small>

The number of high-performance worker threads to run. High-performance workers run intensive jobs like geometric analysis and
file conversion, and use a lot of memory and CPU power. Set to 1 by default, so that demanding jobs don't saturate the Manyfold
server, but if you have lots of CPU and memory available, you can increase this to process more jobs in parallel.

## Miscellaneous

### `MAX_FILE_EXTRACT_SIZE`
<small>Version 0.69.0+</small>

The maximum individual file size (in bytes) that will be extracted from uploaded archives. 1GiB by default.

### `MAX_FILE_UPLOAD_SIZE`
<small>Version 0.69.0+</small>

The maximum individual file size (in bytes) that can be uploaded. 1GiB by default.

### `USAGE_REPORTING_URL`
<small>Version 0.67.0+</small>

Set this URL in order to redirect anonymous usage tracking to your own endpoint; mainly if you want to verify what we're sending. See [the tracking page](tracking.html) for more details.
