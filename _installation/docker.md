---
title: Docker
logo_url: https://cdn.jsdelivr.net/gh/walkxcode/dashboard-icons/svg/docker-moby.svg
layout: installation
order: 1
---

{: .warning }
Before trying to get the app running using this method, we strongly suggest you have some familiarity with [Docker](https://docker.com) and [Docker Compose](https://docs.docker.com/compose/).

[![Built with Depot](https://depot.dev/badges/built-with-depot.svg)](https://depot.dev?utm_source=manyfold)

You can run the latest release in docker by using the image `ghcr.io/manyfold3d/manyfold:latest`. The app also needs a separate database and Redis servers for best performance, but if you're just running a small instance and don't want to run these separately, you can use our all-in-one solo image instead: `ghcr.io/manyfold3d/manyfold-solo:latest`.

The docker images support `linux/amd64`, `linux/arm/v7` and `linux/arm64` architectures, so you should be able to run it on pretty much any computer (PC, Raspberry Pi, Mac, etc).

You can install and run all the dependencies in one go using `docker compose`:

1. Create a file called `docker-compose.yml`, and paste the appropriate (standard or solo) example file below into it. Change the paths, secret key, and database details as necessary.

2. Run `docker compose up`

3. Open Manyfold at <http://localhost:3214>

4. Add a library. Remember the path mappings in the Docker Compose file? In the examples below, the contents of /path/to/your/libraries in your file system would be available in /libraries inside the running app.

## Standard docker-compose.yml

```docker
services:
  app:
    image: ghcr.io/manyfold3d/manyfold:latest
    ports:
      - 3214:3214
    volumes:
      # Uncomment to add a filesystem volume for your model library (or multiple if
      # you want multiple libraries), in the form <local_path>:<container_path>.
      # The local path could be a folder that already contains models, in which case Manyfold
      # will scan and import them, or it could be empty.
      # The container path can be anything; you will need to enter it in the "new library" form.
      # - /local/path/to/your/models:/models
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

## Solo docker-compose.yml

```docker
services:
  app:
    image: ghcr.io/manyfold3d/manyfold-solo:latest
    ports:
      - 3214:3214
    volumes:
      # Uncomment to add a volume where a database file should be created.
      # Don't change the part after the colon, it needs to be at /config
      # - /local/path/to/your/database:/config
      # Uncomment to add a filesystem volume for your model library (or multiple if
      # you want multiple libraries), in the form <local_path>:<container_path>.
      # The local path could be a folder that already contains models, in which case Manyfold
      # will scan and import them, or it could be empty.
      # The container path can be anything; you will need to enter it in the "new library" form.
      # - /local/path/to/your/models:/models
    environment:
      SECRET_KEY_BASE: a_nice_long_random_string
      PUID: 1000
      PGID: 1000
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
