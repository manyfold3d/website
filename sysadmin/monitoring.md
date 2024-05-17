---
title: Monitoring
parent: Running Manyfold
layout: page
nav_order: 2
---

In order to monitor application uptime, you can use the `/health` endpoint.

This is a minimal endpoint that will just return a `200 OK` with the JSON payload `{"status":"OK"}` if the application is running.

Point your uptime monitor at that, and you'll soon know if anything goes badly wrong.
