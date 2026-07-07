---
title: File handlers
parent: Writing Plugins
layout: page
nav_order: 3
---
#### Table of Contents
{:.no_toc}
1. TOC
{:toc}

## Introduction

_File handlers_ are Manyfold's way of choosing what to do with the various files it knows about. Depending on the file format, Manyfold can do server-side rendering, generate open links, display a browser-side 3d rendering, and more. Almost everything Manyfold does goes through a file handler in some way.

There are a few important concepts that all file handlers share:

* `INPUT_TYPES`: a list of media types that the handler can read.
* `OUTPUT_TYPES`: a list of media types that the handler can write.
* `ENVIRONMENTS`: a list of execution environments that the handler can operate in. This is explained more below.

All file handlers are classes derived from `FileHandlers::Base`, and should be in the `FileHandlers` module.; this base class handles most of the work of a file handler, often you just need to fill in the parts specific to your implementation.

```ruby
class FileHandlers::ExampleSlicer < FileHandlers::Base
  ...
end
```

## Input & Output types

{:.important}
More coming soon! See the [file handler](https://github.com/manyfold3d/example_plugin/blob/main/app/lib/file_handlers/example_slicer.rb) in our example plugin in the meantime.
