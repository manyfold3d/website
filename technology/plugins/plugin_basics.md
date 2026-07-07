---
title: Plugin basics
parent: Writing Plugins
layout: page
nav_order: 1
---

#### Table of Contents
{:.no_toc}
1. TOC
{:toc}

## Introduction

Manyfold plugins are, like Manyfold itself, written in Ruby, using the [Rails](https://rubyonrails.org) framework. Each plugin is actually a small [Rails Engine](https://guides.rubyonrails.org/engines.html); however, for many tasks you shouldn't need to know much detail about that.

Plugins, when running, essentially become part of the main Manyfold codebase, so they can do almost anything that's possible. However, it's probably not a good idea to rely on internal code structures that aren't described in this documentation, because they could change at any time.

There's a couple of other caveats; you can't currently add:

* new Ruby dependencies; hopefully in future this will be possible, but for now you're restricted to the gems listed in Manyfold's [Gemfile.lock](https://github.com/manyfold3d/manyfold/blob/main/Gemfile.lock)
* new client-side assets; images, javascript, etc. That should be coming in the near future though.
* database migrations; a settings-storage system for plugins will come in future, and perhaps full database table support if there's demand.

### Using the Template

The simplest way to get started is to use our [plugin template](https://github.com/manyfold3d/plugin-template). Just hit the "use this template" button, then once you have your fork, follow the steps in the [README.md](https://github.com/manyfold3d/plugin-template?tab=readme-ov-file) file to change the name.


## The gemspec

Every plugin must have `gemspec` file in its root folder, which includes all the metadata that describes the plugin, named with the official snake_cased plugin name (e.g. `my_plugin.gemspec`). Plugins MUST set:

* `name` - a human-readable name
* `version` - normally taken from `lib/my_plugin/version.rb`
* `authors` - a list of the authors
* `summary` - a short, 5-10 word description of what the plugin does
* `description` - a longer description
* `homepage` - website or its source code
* `metadata["manyfold_version"]` - a [Gem::Version](https://ruby-doc.org/stdlib-2.3.1/libdoc/rubygems/rdoc/Gem/Version.html) compatible semantic versioning constraint that specifies which versions of Manyfold the plugin will work with. You can specify multiple constraints if you need to, such as `[">= 0.145.0", "< 1.0"]`.

{:.note}
We highly recommend that you adhere to proper [Semantic Versioning](https://semver.org) for your plugin.

## Directory structure

The other pages in this section describe how to accomplish particular things, but we'll start here with an overview of the file structure of a plugin. This is just a brief overview of the parts you'll likely need, but for more detail, see the [Rails documentation](https://guides.rubyonrails.org/getting_started.html#directory-structure).

### The /lib directory

There are a few basic files in the `lib` folder that make the plugin into a Rails engine. Most can be left alone, and if you know enough about Rails engines to start changing them, you don't need our advice here!

In general the only one of these you'll need to touch (after renaming) is `lib/my_plugin/version.rb`, where you can set the version number of your plugin.

### The /app directory

Most of your plugin code will live here. This directory should follow the standard Rails layout, with `controllers` and `views` subdirectories if you are adding [your own pages](/technology/plugins/adding_pages), `components` for [UI components](/technology/plugins/ui_components), or `lib/file_handlers` if you're adding [file handlers](/technology/plugins/file_handlers).

### Initializers

Files in `/config/initializers` are automatically run when Manyfold starts. The example plugin uses these to [register file types](/technology/plugins/file_types) and [UI hooks](/technology/plugins/ui_hooks.md); see those sections for detail. If you want to do other work at initialization time, create a file here and it will be run automatically.

### Locale data

`/config/locales` contains translation strings in YAML files named after the locale (e.g. `en.yml`). We'd recommend that all text in your plugin is loaded from these files using Rails' built in `t()` method, or `translate()` for HTML-free strings that go into HTML attributes. `en` will be used by default if no other translations are available.

```ruby
en:
  my_plugin:
    page:
      title: My page title
```

```ruby
t("my_plugin.page.title")
=> "My page title"
```

See the [Rails guide to custom translation strings](https://guides.rubyonrails.org/i18n.html#how-to-store-your-custom-translations) for more details.

## See also

* [Getting Started with Rails](https://guides.rubyonrails.org/getting_started.html).
* [Rails Internationalization (I18n) API](https://guides.rubyonrails.org/i18n.html)
* [Using Initializer Files](https://guides.rubyonrails.org/configuring.html#using-initializer-files)
* [Getting Started with Engines](https://guides.rubyonrails.org/engines.html)
