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

|Release|Command|
|--|--|
|Offical (standard or solo)|`docker exec -it manyfold /usr/src/app/bin/rails console`|
|Linuxserver|`docker exec -it manyfold sh -c "cd /app/www && bundle exec bin/rails console"`|

You should get an `irb` prompt, and then you're ready.

### Reset admin password

In single user mode, the admin account should already be authenticated and you can browse to `<instance_url>/admin/users` to edit the password of the user. In multiuser mode which should be enabled for public facing sites, this is not possible without risking giving administrative access to anyone accessing the site.

To reset the admin password, perform the following commands in the rails console. Be sure to replace the email and password:

```ruby
u = User.find_by(email: 'root@localhost')
u.password = 'P@$$w0rd!'
u.password_confirmation = 'P@$$w0rd!'
u.save!
```

### Remove all tags

Sometimes scanning an existing library can produce a load of tags you don't want, or just far too many. To remove all tags:

```ruby
ActsAsTaggableOn::Tagging.delete_all
ActsAsTaggableOn::Tag.delete_all
```

### Rescan all models

If parsing metadata from path during scan didn't work as you intended, you might want to force a full rescan to try it again:

```ruby
Model.find_each { |m| Scan::Model::ParseMetadataJob.perform_later(m.id, scan: true) }
```

This might take a while to run if you have a lot of models. The scans will run in the background once queued up.

### Remove all missing files

If you have a file clearout (for instance, deleting a load of pre-sliced files), you might end up with a lot of "missing files" problems in Manyfold after a rescan. Removing these all one by one can be difficult, so you can remove them all in one command by running:

```ruby
Problem.where(problematic_type: "ModelFile", category: :missing).each {|x| x.problematic.destroy}
```

### Remove empty collections

Until the administrative UI can properly handle this, you can delete collections without models included by running:

```ruby
Collection.all.map { |c| unless Model.where(collection_id: c.id).size > 0; c.destroy  end }
```

### Debugging invalid files

Due to the occasional bug, it's possible that a file (or other) record might get in a bad state. To print out details of any with errors, run:

```ruby
ModelFile.find_each { |x| puts "#{x.model.name} / #{x.name}" if !x.valid? }
````

### Test email settings

When setting up an instance for the first time, it can be helpful to test the email settings and adjust as necessary. We can test with the account approved message to the first user account created on the server (`id: 1`). The rails console will report any errors encountered.

```ruby
UserMailer.with(user: User.find(1)).account_approved.deliver_now
```

### Get current version of a loaded Gem

In the course of troubleshooting a specific Gem's functionality, you may need to get the version to confirm that the one loaded in the docker container is the correctly intended version. Adjust the `if` statement with the Gem's name:

```ruby
Gem::Specification.each {|g| puts g.version if g.name == "aws-sdk-s3"};
```
