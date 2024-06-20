---
title: Docker Compose
parent: Get Started
layout: page
nav_order: 1
---

{: .warning }
Before trying to get the app running using this method, we strongly suggest you have some familiarity with [Docker](https://docker.com) and [Docker Compose](https://docs.docker.com/compose/).

[![Built with Depot](https://depot.dev/badges/built-with-depot.svg)](https://depot.dev?utm_source=manyfold)

You can run the latest release in docker by using the image `ghcr.io/manyfold3d/manyfold:latest`. The app also needs a PostgreSQL and Redis database to operate.

The docker image supports `linux/amd64`, `linux/arm/v7` and `linux/arm64` architectures, so you should be able to run it on pretty much any computer (PC, Raspberry Pi, Mac, etc).

You can install and run all the dependencies in one go using `docker compose`:

1. Create a file called `docker-compose.yml`, and paste the example below into it. Change the paths, secret key, and database password.

2. Run `docker-compose up`

3. Open Manyfold at <http://localhost:3214>

4. Add a library. Remember the path mappings in the Docker Compose file? In `docker-compose.example.yml` the libraries at /path/to/your/libraries in your file system would be available at /libraries in the app.

```docker
version: "3"

services:
  app:
    image: ghcr.io/manyfold3d/manyfold:latest
    ports:
      - 3214:3214
    volumes:
      - /path/to/your/libraries:/libraries
    environment:
      DATABASE_URL: postgresql://manyfold:password@db/manyfold?pool=5
      SECRET_KEY_BASE: a_nice_long_random_string
      REDIS_URL: redis://redis:6379/1
      PUID: 1000
      PGID: 1000
      # For details of other optional environment variables, including features such
      # as multiuser mode, visit https://manyfold.app/sysadmin/configuration.html
    depends_on:
      - db
      - redis
    networks:
      - manyfold
    links:
      - db
      - redis

  db:
    image: postgres:15
    volumes:
      - db_data:/var/lib/postgresql/data
    environment:
      POSTGRES_USER: manyfold
      POSTGRES_PASSWORD: password
    restart: on-failure
    networks:
      - manyfold

  redis:
    image: redis:7
    restart: on-failure
    networks:
      - manyfold

volumes:
  db_data:


networks:
  manyfold:
```
