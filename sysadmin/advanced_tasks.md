---
title: Advanced Tasks
parent: Admin Guide
layout: page
nav_order: 9
---

You can do a lot through Manyfold's UI, but because we're still building the app, there are some things that are difficult or time-consuming to do. This page lists some useful tasks that you can perform via a command-line interface instead.

{:.important}
These commands are for advanced use only and are somewhat risky. You can easily break your system or lose data if you get them wrong. Be careful!

## Rails Console Commands

All the commands below are run in the Rails console. To open the console, run something like this on the machine hosting your Manyfold server, substituting the appropriate paths and container names for your system:

```sh
docker exec -it manyfold /usr/src/app/bin/rails console
```

You should get an `irb` prompt, and then you're ready.

### Remove all tags

Sometimes scanning an existing library can produce a load of tags you don't want, or just far too many. To remove all tags:

```ruby
ActsAsTaggableOn::Tagging.delete_all
ActsAsTaggableOn::Tag.delete_all
```

### Rescan all models

If parsing metadata from path during scan didn't work as you intended, you might want to force a full rescan to try it again. First, you'll want to remove all tags, otherwise metadata won't be populated; then, run:

```ruby
Model.find_each { |m| Scan::CheckModelJob.perform_later(m.id, scan: true) }
```

This might take a while to run if you have a lot of models. The scans will run in the background once queued up.

### Remove all missing files

If you have a file clearout (for instance, deleting a load of pre-sliced files), you might end up with a lot of "missing files" problems in Manyfold after a rescan. Removing these all one by one can be difficult, so you can remove them all in one command by running:

```ruby
Problem.where(problematic_type: "ModelFile", category: :missing).each {|x| x.problematic.destroy}
```

### Debugging invalid files

Due to the occasional bug, it's possible that a file (or other) record might get in a bad state. To print out details of any with errors, run:

```ruby
ModelFile.find_each { |x| puts "#{x.model.name} / #{x.name}" if !x.valid? }
````
