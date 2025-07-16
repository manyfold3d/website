---
title: Supported Formats
parent: User Guide
layout: page
nav_order: 10
---

Manyfold will index lots of different file formats. This page gives the full list, as well as what can be shown in the previews in the Web UI. Files not in these lists will be ignored.

Note that `x-` MIME types are unofficial and may not be used anywhere except within Manyfold.

To request support for another file format, please [open a feature request](https://github.com/manyfold3d/manyfold/issues/new/choose)

## 3D Models

|File type|Extensions|MIME type|Preview|Analyse|
|--|--|--|--|--|
|3D Studio|`*.3ds`, `*.max`|`application/x-3ds`, `image/x-3ds`|✅||
|3MF|`*.3mf`|`model/3mf`|✅||
|AMF|`*.amf`|`application/x-amf`|||
|Alembic|`*.abc`|`model/x-alembic`|||
|Autodesk DWG|`*.dwg`|`image/vnd.dwg`|||
|Autodesk DXF|`*.dxf`|`image/vnd.dxf`|||
|Autodesk Inventor|`*.iam`, `*.ipt`|`model/x-inventor-part`, `model/x-inventor-assembly`|||
|BRep|`*.brep`|`model/x-brep`|||
|Blender|`*.blend`|`model/x-blender`|||
|Cheetah3D|`*.jas`|`model/x-cheetah3d`|||
|Collada|`*.dae`|`model/vnd.collada+xml`|||
|DRACO|`*.drc`|`model/vnd.google.draco`|✅||
|Filmbox|`*.fbx`|`model/x-fbx`|✅||
|FreeCAD|`*.fcstd`|`model/x-freecad`|||
|Fusion360|`*.f3d`, `*.f3z`|`model/x-fusion`|||
|GLTF|`*.gltf`, `*.glb`|`model/gtlf+json`, `model/gtlf+binary`|✅||
|HueForge|`*.hfp`|`model/x-hfp`|||
|IGES|`*.iges`, `*.igs`|`model/iges`|||
|LDraw|`*.ldr`, `*.mpd`|`application/x-ldraw`|✅||
|Maya|`*.ma`, `*.mb`|`model/x-maya`|||
|Meshmixer|`*.mix`|`model/x-meshmixer`|||
|Modo|`*.lxo`|`model/x-modo`|||
|OpenSCAD|`*.scad`|`application/x-openscad`|||
|PLY|`*.ply`|`model/x-ply`|✅||
|STEP|`*.step`, `*.stp`|`model/x-step`|||
|STL|`*.stl`|`model/stl`|✅|✅|
|Sketchup|`*.skp`|`model/x-sketchup`|||
|Solidworks|`*.sldprt`|`model/x-solidworks-part`|||
|Speedtree|`*.spm`|`model/x-speedtree`|||
|VRML|`*.wrl`|`model/vrml`|||
|Wavefront OBJ|`*.obj`, `*.mtl`|`model/obj`|✅|✅|
|X3D|`*.x3d`|`model/x3d`|||


## Print & Slicer files

|File type|Extensions|MIME type|Preview|
|--|--|--|--|
|Chitubox|`*.chitubox`, `*.ctb`|`model/x-chitubox`||
|GCode|`*.gcode`|`model/x-gcode`|✅|
|Lychee|`*.lys`, `*.lyt`|`model/x-lychee`||

## Images

|File type|Extensions|MIME type|Preview|
|--|--|--|--|
|BMP|`*.bmp`|`image/bmp`|✅|
|GIF|`*.gif`|`image/gif`|✅|
|JPEG|`*.jpg`, `*.jpeg`, `*.jpe`, `*.pjpeg`|`image/jpeg`|✅|
|PNG|`*.png`|`image/png`|✅|
|SVG|`*.svg`|`image/svg+xml`|✅|
|TIFF|`*.tiff`, `*.tif`|`image/tiff`|✅|
|WebP|`*.webp`|`image/webp`|✅|

## Video

|File type|Extensions|MIME type|Preview|
|--|--|--|--|
|MP4|`*.mp4`, `*.m4v`|`video/mp4`|✅|
|MPEG|`*.mpeg`, `*.mpg`, `*.mpe`|`video/mpeg`|✅|
|WebM|`*.webm`|`video/webm`|✅|

## Documents

|File type|Extensions|MIME type|Preview|
|--|--|--|--|
|HTML|`*.html`|`text/html`||
|Markdown|`*.md`|`text/markdown`|✅|
|Microsoft Word|`*.doc`, `*.docx`|`application/msword`, `application/vnd.openxmlformats-officedocument.wordprocessingml.document`||
|PDF|`*.pdf`|`application/pdf`|✅|
|Text|`*.txt`, `*.text`|`text/plain`|✅|

## Archives

|File type|Extensions|MIME type|
|--|--|--|
|7-Zip|`*.7z`|`application/x-7z-compressed`|
|bzip2|`*.bz2`|`application/x-bzip2`|
|gzip|`*.gzip`, `*.gz`|`application/gzip`|
|RAR|`*.rar`|`application/x-rar-compressed`|
|ZIP|`*.zip`|`application/zip`|

## Other

|File type|Extensions|MIME type|
|--|--|--|
|Binary blobs|`*.bin`|`application/octet-stream`|
|Excellon|`*.drl`|`application/x-excellon`|
|Gerber|`*.grb`, `*.gerber`, `*.geb`, `*.gb`, `*.grbjob`|`application/x-gerber`, `application/vnd.gerber`, `application/x-gerber-job`|
|KiCad|`*.kicad_pro`, `*.kicad_mod`, `*.kicad_pcb`, `*.kicad_sym`, `*.kicad_sch`, `*.kicad_wks`|`application/x-kicad-*`|
