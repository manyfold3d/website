---
title: File types
parent: Writing Plugins
layout: page
nav_order: 2
---

Manyfold knows about a lot of [file types](/manual/supported_formats), but plugins can register their own. All files that match a registered file type will be detected and indexed during scans.

To register a new file type, add a `config/initializers/media_types.rb` file to your plugin, and add the following for each type you want to add:

```ruby
# Simple format with one media type and one extension
MediaType.register("model/stl", :stl, category: :model)

# You can define additional extensions and media types if needed
MediaType.register(
	"model/step",
	:step,
	additional_types: ["model/step+xml", "application/vnd.step"],
	additional_extensions: ["stp", "stpnc"],
	category: :model
)
```

As you can see, each file type needs the following:

* One or more media types (`model/stl` above)
* One or more file extensions (`:stl` above)
* A category (see below)

If the file type has more than one media type or extension, add them in the additional parameters. See [media_types.rb] in the example plugin for a working example.

## Categories

So that Manyfold knows how to treat a file type, each type has a `category` (`:model` in the example above). Valid categories are:

|Category|Description|
|-|-|
|`:model`|3d files; models, scenes, etc; e.g. STL|
|`:slicer`|3d files in a format ready to be printed - not normally human-viewable; e.g. GCODE, SL1, GOO|
|`:image`|Image files; e.g. JPG|
|`:video`|Video files; e.g. MP4|
|`:archive`|Compressed archives; e.g. ZIP or RAR files|
|`:document`|Documents, text and other formats; e.g. PDFs, Markdown, KiCAD|

Note that for Manyfold's purposes the media type may not reflect the category you want to use; for instance, even though DXF files are `image/dxf`, Manyfold treats them as `:model`.

## See also

* [Documentation for MediaType#register](https://rubydoc.info/github/manyfold3d/manyfold/MediaType#register-class_method)
* [Built-in type definitions](https://github.com/manyfold3d/manyfold/blob/main/config/initializers/register_media_types.rb)
