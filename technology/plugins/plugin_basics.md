---
title: Plugin basics
parent: Writing Plugins
layout: page
nav_order: 1
---


Plugins, when running, essentially become part of the main Manyfold codebase, so they can do almost anything that's possible. However, it's probably not a good idea to rely on internal code structures that aren't described below, because they could change at any time. There's a couple of other caveats:

* You can't currently add new Ruby dependencies; hopefully in future this will be possible, but for now you're restricted to the gems listed in Manyfold's [Gemfile.lock](https://github.com/manyfold3d/manyfold/blob/main/Gemfile.lock)
* You can't currently add new client-side assets; images, javascript, etc. That should be coming in the near future though.
