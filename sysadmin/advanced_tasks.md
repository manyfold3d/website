---
title: Advanced Tasks
parent: Admin Guide
layout: page
nav_order: 9
---

You can do a lot through Manyfold's UI, but sometimes you might need to do some one-off maintenance. This page lists some useful tasks that you can perform via a command-line interface instead.

## Manyfold CLI

The `bin/manyfold` command-line interface (CLI) allows you to perform various maintenance tasks. You will need to run it inside your docker container, like so:

|Release|Command|
|--|--|
|Offical (standard or solo)|`docker exec -it manyfold bundle exec /usr/src/app/bin/manyfold {command}`|
|Linuxserver|`docker exec -it manyfold sh -c "cd /app/www && bundle exec bin/manyfold {command}"`|

The available commands are:

|Command / Subcommand|Description|
|---|---|
|`help`|List available commands|
|`help {command}`|List available subcommands|
|`collections prune`|Removes all empty collections|
|`creators prune`|Removes all creators with no models|
|`email test`|Sends a test email to the main admin account address, to check email delivery is working|
|`jobs unlock`|Remove stale exclusivity locks that might be preventing background jobs running.
|`libraries scan`|Run a filesystem scan on all libraries. To scan a single library, add `--name=...` with the name of the library to scan.|
|`links deduplicate`|Removes duplicated links. The same link in different models/creators/collections is kept, but any of the same link in the same object will be removed.|
|`links purge`|Remove all links that match the supplied text (e.g. `--match=localhost`).|
|`links sync`|Run synchronisation process for links to other sites; add `--match=...` to only sync links that match the supplied text (e.g. `--match=thingiverse.com`).|
|`models update_metadata`|Rerun metadata parsing for all models. If parsing metadata from path during scan didn't work as you intended, you might want to force a full rescan to try it again. This might take a while to run if you have a lot of models. The scans will run in the background once queued up. Add the `--search="..."` option to specify a subset of models to update, using the same query syntax as the built-in search box|
|`model pregenerate_downloads`|Generate ZIP download files for all models, including all download variants. This will easily at least double your disk usage, so use with caution. Add the `--search="..."` option to specify a subset of models to pregenerate, using the same query syntax as the built-in search box|
|`problems prune`|Remove any problems that don't have an associated object; this can happen sometimes due to old bugs or database manipulation.|
|`problems purge`|Remove all problem records. Problems that are still valid will reappear on rescan, but this can be helpful if you've made large changes to your library and have a lot of "missing file" problems.|
|`tags purge`|Remove all tags. Sometimes scanning an existing library can produce a load of tags you don't want, or just far too many. You may want to do this if you've run metadata extraction with the wrong path template and ended up with loads of tags you don't want.|
|`users approve --email={account_email}`|Approve a pending user account if you can't access the UI in order to do so in the normal way.|
|`users password --email={account_email}`|Set the password for the specified account; this includes the ability to reset the password for the administrator account.|

## Rails Console Commands

If you want to do something that's not available in the CLI tool, you can run code directly in the Rails console.

{:.important}
These commands are for advanced use only and are somewhat risky. You can easily break your system or lose data if you get them wrong. Be careful!

To open the console, run something like this on the machine hosting your Manyfold server, substituting the appropriate paths and container names for your system:

|Release|Command|
|--|--|
|Offical (standard or solo)|`docker exec -it manyfold /usr/src/app/bin/rails console`|
|Linuxserver|`docker exec -it manyfold sh -c "cd /app/www && bundle exec bin/rails console"`|

You should get an `irb` prompt, and then you're ready.

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

### Get current version of a loaded Gem

In the course of troubleshooting a specific Gem's functionality, you may need to get the version to confirm that the one loaded in the docker container is the correctly intended version. Adjust the `if` statement with the Gem's name:

```ruby
Gem::Specification.each {|g| puts g.version if g.name == "aws-sdk-s3"};
```
