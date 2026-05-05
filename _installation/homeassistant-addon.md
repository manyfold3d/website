---
title: Home Assistant Addon
logo_url: https://cdn.jsdelivr.net/gh/walkxcode/dashboard-icons/svg/home-assistant.svg
layout: installation
---


You can run Manyfold on your Home Assistant server by using this non-official collection of addon repository by [alexbelgium](https://github.com/alexbelgium/hassio-addons), based on the official solo Docker image of Manyfold. Alternatively you can use the single addon repository from [toledoem](https://github.com/ToledoEM/ManyFoldHA_app).

## Installation

1. Add the add-ons repository to your home assistant instance (in supervisor addons store at top right, or click button below if you have configured my HA)
   [![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Falexbelgium%2Fhassio-addons)
2. Refresh Add-on Store and install **Manyfold**.
3. Configure options (defaults are safe for first run):
   - `library_path`: `/share/manyfold/models`
   - `secret_key_base`: leave blank to auto-generate
   - `puid` / `pgid`: set to a non-root UID/GID (see "Fix root warning (PUID/PGID)" below)
   - optionally tune worker/thread and upload limits in "Small server tuning" below
4. Start the add-on.
5. Open `http://<HA_IP>:3214`.

## Options

- `secret_key_base`: App secret used by Rails to sign/encrypt sessions and tokens.
- `puid` / `pgid`: Ownership applied to writable mapped directories (`/config` paths).
- `multiuser`: Toggle Manyfold multiuser mode.
- `library_path`: Scanned/indexed path.
- `thumbnails_path`: Persistent thumbnails/index artifacts (must be under `/config`).
- `log_level`: `info`, `debug`, `warn`, `error`.
- `web_concurrency`: Puma worker process count.
- `rails_max_threads`: Max threads per Puma worker.
- `default_worker_concurrency`: Sidekiq default queue concurrency.
- `performance_worker_concurrency`: Sidekiq performance queue concurrency.
- `max_file_upload_size`: Max uploaded archive size in bytes.
- `max_file_extract_size`: Max extracted archive size in bytes.


## Installation guides

- [Install guide](https://github.com/alexbelgium/hassio-addons/blob/master/manyfold/README.md)
- Home-Assistant Addon issues [github](https://github.com/alexbelgium/hassio-addons/issues) and tag @ToledoEM
