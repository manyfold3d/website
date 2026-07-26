---
title: Railway
logo_url: https://cdn.jsdelivr.net/gh/walkxcode/dashboard-icons/svg/railway.svg
layout: installation
---

You can deploy Manyfold on [Railway](https://railway.com) with a community-maintained one-click template. It wires the **standard** stack (not solo): Manyfold app, PostgreSQL, and Redis.

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/deploy/manyfold?utm_medium=integration&utm_source=button&utm_campaign=manyfold)

After deploy:

1. Open the **app** public URL (Postgres and Redis stay private).
2. Set your administrator password when prompted.
3. Create a library pointed at `/models` (the mounted volume).

Optional features (federation, OIDC, SMTP, and so on) use the same environment variables as Docker — see [configuration](/sysadmin/configuration.html).

This template is **community-maintained** (deployment config only), not an official Manyfold offering. Template source: [osbytes/template-manyfold](https://github.com/osbytes/template-manyfold). Report template issues there; report Manyfold bugs via the usual [GitHub issues](https://github.com/manyfold3d/manyfold/issues) channel.
