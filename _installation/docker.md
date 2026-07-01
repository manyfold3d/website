---
title: Docker
logo_url: https://cdn.jsdelivr.net/gh/walkxcode/dashboard-icons/svg/docker-moby.svg
layout: installation
order: 1
---

{: .warning }
Before trying to get the app running using this method, we strongly suggest you have some familiarity with [Docker](https://docker.com) and [Docker Compose](https://docs.docker.com/compose/).

[![Built with Depot](https://depot.dev/badges/built-with-depot.svg)](https://depot.dev?utm_source=manyfold)

There are two separate docker images: standard and "solo":

<div class="card-list col-2" id="now">
  <div style="position: relative">
    <div>
      <h3>Solo: the simplest setup</h3>
      <ul>
        <li><code>manyfold3d/manyfold-solo:latest</code></li>
        <li><code>ghcr.io/manyfold3d/manyfold-solo:latest</code></li>
      </ul>
    </div>
    <div>
      <p style="margin-bottom: 3em">
        A single all-in-one container that runs everything you need, including database and Redis
      </p>
    </div>
    <div style="position: absolute; bottom: 0.5em; right: 1em">
      <a href="#solo-docker-composeyml" type="button" class="btn btn-purple">View compose file</a>
    </div>
  </div>
  <div style="position: relative">
    <div>
      <h3>Standard: scalable performance</h3>
      <ul>
        <li><code>manyfold3d/manyfold:latest</code></li>
        <li><code>ghcr.io/manyfold3d/manyfold:latest</code></li>
      </ul>
    </div>
    <div>
      <p style="margin-bottom: 3em">
        More control; requires a separate database server such as PostgresSQL, and a separate Redis server.
      </p>
    </div>
    <div style="position: absolute; bottom: 0.5em; right: 1em">
      <a href="#standard-docker-composeyml" type="button" class="btn btn-purple">View compose file</a>
    </div>
  </div>
</div>

All docker images support `linux/amd64` and `linux/arm64` architectures, so you should be able to run it on pretty much any computer (PC, Raspberry Pi, Mac, etc).

You can install and run all the dependencies in one go using `docker compose`:

1. Create a file called `docker-compose.yml`, and paste the appropriate (standard or solo) example file below into it. Change the paths, secret key, and database details as necessary.

2. Run `docker compose up`

3. Open Manyfold at <http://localhost:3214>

4. Add a library. Remember the path mappings in the Docker Compose file? In the examples below, the contents of `/local/path/to/your/models` in your file system would be available in `/models` inside the running app.

## Solo docker-compose.yml

A single all-in-one container that runs everything you need, including database and Redis

```yaml
services:
  app:
    # See above for a full list of other image sources, e.g. GHCR
    image: manyfold3d/manyfold-solo:latest
    ports:
      - 3214:3214
    volumes:
      # Add a volume where a database file should be created. Plugins are also stored here.
      # IMPORTANT: Don't change the part after the colon, it needs to be at /config
      - /local/path/to/your/database:/config
      # Add a filesystem volume for your model library (or multiple if
      # you want multiple libraries), in the form <local_path>:<container_path>.
      # The local path could be a folder that already contains models, in which case Manyfold
      # will scan and import them, or it could be empty.
      # The container path can be anything; you will need to enter it in the "new library" form.
      - /local/path/to/your/models:/models
    environment:
      SECRET_KEY_BASE: a_nice_long_random_string
      PUID: 1000
      PGID: 1000
      # For details of other optional environment variables, including features such
      # as multiuser mode, visit https://manyfold.app/sysadmin/configuration.html
    restart: unless-stopped
    # Optional, but recommended for better security
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

## Standard docker-compose.yml

More control; requires a separate database server such as PostgresSQL, and a separate Redis server.

```yaml
services:
  app:
    # See above for a full list of other image sources, e.g. GHCR
    image: manyfold3d/manyfold:latest
    ports:
      - 3214:3214
    volumes:
      # Add a filesystem volume for your model library (or multiple if
      # you want multiple libraries), in the form <local_path>:<container_path>.
      # The local path could be a folder that already contains models, in which case Manyfold
      # will scan and import them, or it could be empty.
      # The container path can be anything; you will need to enter it in the "new library" form.
      - /local/path/to/your/models:/models
      # If you want to use any plugins, you will also need a persistent plugins folder.
      # /usr/src/app/plugins is the default, but you can set a different path using the
      # PLUGINS_PATH environment variable.
      - /local/path/to/plugins:/usr/src/app/plugins
    environment:
      DATABASE_ADAPTER: postgresql # mysql2 or sqlite3 are also supported
      DATABASE_HOST: postgres-server
      DATABASE_PORT: 5432 # only needed for non-standard ports
      DATABASE_NAME: manyfold # or the path to the database file if using sqlite3
      DATABASE_USER: manyfold
      DATABASE_PASSWORD: password
      SECRET_KEY_BASE: a_nice_long_random_string
      REDIS_URL: redis://redis-server:6379/1
      PUID: 1000
      PGID: 1000
      # For details of other optional environment variables, including features such
      # as multiuser mode, visit https://manyfold.app/sysadmin/configuration.html
    restart: unless-stopped
    depends_on:
      - postgres-server
      - redis-server
    networks:
      - manyfold
    # Optional, but recommended for better security
    security_opt:
      - no-new-privileges:true
    cap_drop:
      - ALL
    cap_add:
      - CHOWN
      - DAC_OVERRIDE
      - SETUID
      - SETGID

  postgres-server:
    image: postgres:15
    volumes:
      - db_data:/var/lib/postgresql/data
    environment:
      POSTGRES_USER: manyfold
      POSTGRES_PASSWORD: password
    restart: unless-stopped
    networks:
      - manyfold

  redis-server:
    image: redis:7
    restart: unless-stopped
    networks:
      - manyfold

volumes:
  db_data:

networks:
  manyfold:
```
