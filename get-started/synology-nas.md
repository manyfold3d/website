---
title: Synology NAS
parent: Get Started
layout: page
---

{: .important }
NOTE: Your Synology NAS will need to be running Kernel 4.x or higher; the app will not start on kernel version 3. See the "Outdated Synology NAS Kernel under Version 4" section of [Mariushosting's troubleshooting guide](https://mariushosting.com/synology-common-docker-issues-and-fixes) for more info.

You can run Manyfold on your Synology NAS by using the docker-compose template below with [Container Manager](https://www.wundertech.net/container-manager-on-a-synology-nas/) on DSM 7.2+. Alternatively you can use the same template with Portainer if you're running that, or on the command line if you prefer.

The following configuration is tested and working on a DiskStation 923+ with lots of memory and space; you may want to adjust the memory limits to suit your own device.

## docker-compose.yaml

```yaml
version: "3.9"
services:
  manyfold:
    image: ghcr.io/manyfold3d/manyfold:latest
    container_name: Manyfold
    hostname: manyfold
    mem_limit: 8g
    cpu_shares: 2048
    cap_drop:
      - ALL
    cap_add:
      - CHOWN
      - SETUID
      - SETGID
    security_opt:
      - no-new-privileges:true
    healthcheck:
      test: wget --no-verbose --tries=1 --spider http://localhost:3214/health
    ports:
      - 7214:3214
    volumes:
      - /volume1/homes/<YOUR USER NAME>/<YOUR FOLDER FULL OF STUFF>:/libraries:rw
    environment:
      REDIS_URL: redis://:redispass@manyfold-redis:6379/1
      DATABASE_URL: postgresql://manyfolduser:manyfoldpass@manyfold-db/manyfold?pool=5
      SECRET_KEY_BASE: <YOUR KEY>
      PUID: <YOUR ID>
      PGID: <YOUR GID>
    restart: on-failure:5
    depends_on:
      redis:
        condition: service_healthy
      db:
        condition: service_healthy

	redis:
    image: redis:7
    command:
      - /bin/sh
      - -c
      - redis-server --requirepass redispass
    container_name: Manyfold-REDIS
    hostname: manyfold-redis
    mem_limit: 256m
    mem_reservation: 50m
    cpu_shares: 768
    ports:
      - 6379:6379
    security_opt:
      - no-new-privileges:true
    read_only: true
    healthcheck:
      test: ["CMD-SHELL", "redis-cli ping || exit 1"]
    volumes:
      - /volume1/docker/manyfold/redis:/data:rw
    restart: on-failure:5

  db:
    image: postgres:16
    container_name: Manyfold-DB
    hostname: manyfold-db
    mem_limit: 512m
    cpu_shares: 768
    security_opt:
      - no-new-privileges:true
    healthcheck:
      test: ["CMD", "pg_isready", "-q", "-d", "manyfold", "-U", "manyfolduser"]
      timeout: 45s
      interval: 10s
      retries: 10
    volumes:
      - /volume1/docker/manyfold/db:/var/lib/postgresql/data:rw
    environment:
      POSTGRES_DB: manyfold
      POSTGRES_USER: manyfolduser
      POSTGRES_PASSWORD: manyfoldpass
    restart: on-failure:5
```

## Third-party guides

Many people have successfully used Manyfold on their Synology NAS servers, and some have written articles on how to do it. Note that these might be a little out of date with more recent versions:

* Mariushosting has written [a very comprehensive guide](https://mariushosting.com/how-to-install-manyfold-on-your-synology-nas/).
* Andy Piper has shared some details of his experience on [his website](https://andypiper.co.uk/2023/07/05/running-a-3d-print-catalogue-with-van-dam/).
