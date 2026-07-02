---
title: Running Plugins
parent: Admin Guide
layout: page
nav_order: 2
---

{:.note}
Plugins are a very new feature! Please [report any bugs](https://github.com/manyfold3d/manyfold/issues/new?template=bug_report.md) you come across.

Manyfold has a lot of built-in features, but since version 0.146.0 it's also supported *plugins*, small optional extensions which add additional functionality. Plugins can add elements to the user interface, add additional file types or API connections, and a lot more.

This page explains how to install and manage plugins. If you want to create your own plugin, read the [developer documentation](/technology/plugins).

{:.important}
Manyfold plugins can access all the data, files, and code on your instance. Make sure you trust any plugin that you install!

## Configuring your instance

{:.info}
If you're using our `solo` instance, no configuration is required, plugins will be stored in your config folder along with your database file.

Plugin code is separate from the main application code, so needs to be stored somewhere different. Because of this, in order to use plugins, you need to ensure that the plugins folder is writable and won't be lost when the container is updated (assuming you're using Docker).

As shown in our example docker compose files, you need to mount a persistent volume of some sort on the right path.

### Default

Unless otherwise specified, the plugins directory should be mounted at `/usr/src/app/plugins`, and must be writable by the application user (`PUID`). Note that this path is correct for our standard image; if you're using linuxserver, or another image, refer to their documentation for the correct default.

### Custom path

You can set your own path using the `PLUGINS_PATH` environment variable. Set the variable to the path in the docker container where you're mounting the plugin volume.

## Finding plugins

Visit our [plugin list](/plugins) to see what's available.

## Installing plugins

Once you have storage set up, you can install plugins on the `Plugins` page in the admin settings area.

1. Download the latest release source code zipfile for the plugin you want.
2. Upload the zipfile using the form on the plugins page.
3. Restart your Manyfold server.

## Updating plugins

If you upload a zipfile with the same name as before, it will overwrite the existing plugin. Restart your Manyfold server after updating.

{:.note}
GitHub downloads tend to have the version number in them, which means you might end up with two copies of a plugin at once. If so, remove the older one manually (see below). We'll be improving this soon.

## Removing plugins

Currently plugin removal is manual; just remove the directory from the plugins folder by hand, and restart your Manyfold server.

## Troubleshooting

If your Manyfold instance fails to restart after installing a plugin, remove the plugin and report a bug via the plugin's issue tracker. Include logfile output if you can, that will definitely help.

If you've recently updated Manyfold and it won't start but you've not changed any plugins, first remove plugins one by one see if that isolates the problem, then report a bug via the [Manyfold issue tracker](https://github.com/manyfold3d/manyfold/issues/new?template=bug_report.md). Again, include logfile output if you can!

{:.note}
We know this is a bit awkward, and will be adding some better error handling soon. Thanks for your patience!
