---
title: Monitoring
parent: Admin Guide
layout: page
nav_order: 2
---

In order to monitor application uptime, you can use the `/health` endpoint.

This is a built in rails health check that will just return a `200 OK` and a green screen in your browser if the application is running.

Point your uptime monitor at that, and you'll soon know if anything goes badly wrong.
