---
title: Supported Formats
parent: Using Manyfold
layout: page
nav_order: 1
---

Manyfold will index lots of different file formats. This page gives the full list, as well as what can be shown in the previews in the Web UI. Files not in these lists will be ignored.

Note that `x-` MIME types are unofficial and may not be used anywhere except within Manyfold.

To request support for another file format, please [open a feature request](https://github.com/manyfold3d/manyfold/issues/new/choose)

## 3D Models

|File type|Extensions|MIME type|Preview|Analyse|
|--|--|--|--|
|3MF|`*.3mf`|`model/3mf`|✅||
|Alembic|`*.abc`|`model/x-alembic`|||
|Blender|`*.blend`|`model/x-blender`|||
|Meshmixer|`*.mix`|`model/x-meshmixer`|||
|OpenSCAD|`*.scad`|`model/x-openscad`|||
|PLY|`*.ply`|`model/3mf`|✅||
|STEP|`*.step`, `*.stp`|`model/x-step`|||
|STL|`*.stl`|`model/stl`|✅|✅|
|Wavefront OBJ|`*.obj`|`model/obj`|✅|✅|

## Print & Slicer files

|File type|Extensions|MIME type|Preview|
|--|--|--|
|Chitubox|`*.chitubox`, `*.ctb`|`model/x-chitubox`||
|GCode|`*.gcode`|`model/x-gcode`||
|Lychee|`*.lys`, `*.lyt`|`model/x-lychee`||

## Images

|File type|Extensions|MIME type|Preview|
|--|--|--|
|BMP|`*.bmp`|`image/bmp`|✅|
|GIF|`*.gif`|`image/gif`|✅|
|JPEG|`*.jpg`, `*.jpeg`, `*.jpe`, `*.pjpeg`|`image/jpeg`|✅|
|PNG|`*.png`|`image/png`|✅|
|SVG|`*.svg`|`image/svg+xml`|✅|
|TIFF|`*.tiff`, `*.tif`|`image/tiff`|✅|
|WebP|`*.webp`|`image/webp`|✅|
