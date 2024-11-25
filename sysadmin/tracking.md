---
title: Tracking
parent: Admin Guide
layout: page
nav_order: 4
---

Since v0.67.0, Manyfold includes an opt-in anonymous usage tracking option. This has been designed to let the developers answer one single question; how many people are running Manyfold instances?

The system has been designed to be as minimal and private as possible. User privacy is incredibly important to us, and data harvesting is the scourge of the Internet.

{:.info}
Usage statistics are *really* useful to the developers. PLEASE turn this feature on if you are comfortable doing so!

On the settings page, you will find a new panel for usage tracking. If an admin enables this option for the site, then once a day, a small JSON payload is POSTed to a custom data collection API.

## Collected data

The complete payload is:

```json
{
	"id":"fdb45536-cba8-4204-b352-71fc1062fd95",
	"version": {
		"app":"v0.67.0",
		"sha":"f8d09c9be141e9fb367b08099308dd8b93aa92b2",
		"image":"ghcr.io/manyfold3d/manyfold",
		"arch":"arm-linux-musleabihf"
	}
}
```

These fields are:

* `id`: A randomly-generated UUID unique to your system. If tracking is disabled, this ID is immediately deleted from your system, and if you enabled tracking again, a new one is generated. Before you turn on tracking, this will be `null`.
* `app`: The version of Manyfold that you're running, as shown in the footer. This will be the Docker tag you're using, or "unknown" if you're running a development version.
* `sha`: The git SHA of the running code, again as shown in the app footer. This specifies the precise software version, and is really just a double-check on the `app` number.
* `image`: The name of the prebuilt docker image you're running. This could be the standard image, `manyfold-solo`, or the linuxserver image. If you build your own, nothing will show here.
* `arch`: The system architecture as reported by Ruby's built-in RUBY_PLATFORM constant.

No other information is sent in the request payload. You can verify this by sending the data to your own endpoint by setting the `USAGE_REPORTING_URL` environment variable. For instance, you could send it to something like a [RequestBin](https://requestbin.myworkato.com/) and see exactly what arrives.

## Tracking API

The tracking API is hosted at [tracking.manyfold.app](https://tracking.manyfold.app) (which redirects to this page by default if you visit with a browser), and all its source code is on GitHub at [github.com/manyfold3d/tracking](https://github.com/manyfold3d/tracking).

The API code is designed to be as forgetful as possible. There is *no* persistent storage, and data is never written to disk, even temporarily. The API stores all the submitted data in memory, so when it's restarted, everything is gone.

The API provides two endpoints for reading data back, both of which are open to anyone to check:

* `/stats` provides aggregated statistics in JSON format; the number of instances, and a breakdown by version so we can track rollout.
* `/badge` provides a shields.io badge URL from the aggregated stats. Here it is: ![Manyfold instance count](https://tracking.manyfold.app/badge)

Because all data is in-memory, there is literally no other way for anyone to get data out, not even the Manyfold developers who run the API. This also leads to the privacy benefit that the API code cannot be changed without resetting all data.

## Security

Because all data is anonymous and transient, there is intentionally no security at all (other than HTTPS security in transit). You could pollute our data as much as you like, if you wanted to - all it would do is inflate our usage figures, which is our problem, not yours.

## Log Retention

The tracking API is hosted on [Render](https://render.com). Request IP addresses *are* temporarily stored in application logs, but are only retained for 7 days. If we can find a way to reduce this or remove the IP addresses, we will.
