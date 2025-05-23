---
title: Packaging
parent: Technology
layout: page
nav_order: 1
---
3D print models inherently have associated metadata, such as license, description, links, keywords and so on. However, this metadata is rarely included in model downloads, and certainly not in a machine-readable structured format. This page proposes that [Data Package](https://datapackage.org/) be adopted as a standard packaging format for 3d print models, so that this metadata can be included along with the model files themselves; we also define the Manyfold 3D Data Package Profile, a JSON schema extension, for application-specific metadata.

Manyfold will follow this standard in our downloads and in upload parsing, and we invite other hosting sites to do the same.

## Summary

A 3d model download (normally a zip file that includes mutiple 3d files) should be a valid [Data Package](https://datapackage.org/); i.e. it should include a `datapackage.json` file in the root folder, as well as the model files themselves.

For complete discussion of the Data Package format, see the [official standard](https://datapackage.org/standard/data-package/); here we present a summary of the format as applied to a 3d print model download. See the end of this document for a [complete example](#complete-example) `datapackage.json` file.

## General metadata fields

The `datapackage.json` file should contain a number of general metadata fields, all of which are optional though recommended:

|Field|Description|
|--|--|
|`title`|The human name of the model, e.g. "Stanford Bunny".|
|`name`|A URL-safe version of the model name, such as might be used in a URL path, e.g. "stanford-bunny"|
|`description`|A textual description of the model. Can include `\n` line break characters and markdown formatting.|
|`homepage`|The canonical URL of the model; in the case of downloads, most likely the page the file was downloaded from.|
|`image`|A path within the package for an image which shows a preview of the model.|
|`keywords`|An array of keyword terms; this could be equivalent to "tags" on many hosting sites. e.g. `["rabbit", "statue"]`.|

### Example

```json
{
	"$schema": "https://manyfold.app/profiles/0.0/datapackage.json",
	"name": "40k-deployment-zone-markers",
	"title": "40k Deployment Zone Markers",
	"description": "A set of boundary markers that you can use for deployment zones in 40k games.\n\nPrinting four corners, four curves and maybe twelve straights will be enough for a two deployment zones.",
	"homepage": "https://manyfold.floppy.org.uk/models/pkq8x0h7",
	"image": "markers.png",
	"keywords": [
		"40k",
		"deployment",
		"markers"
	],
	...
}
```

## License

The file should include license details for the model, using [SPDX license identifiers](https://spdx.org/licenses/). The `licenses` key in `datapackage.json` is an array of license definitions, so more than one license can be applied.

Each license in the array should include:

|Field|Description|
|--|--|
|`name`|The SPDX license identifier, e.g. "CC-BY-SA-4.0"|

It may also optionally include:

|Field|Description|
|--|--|
|`path`|a URL for the license, e.g. "https://creativecommons.org/licenses/by-sa/4.0/"|
|`title`|A human-readable name for the license, e.g. "Creative Commons Attribution Share Alike 4.0 International"|

For models that do not have a license set, the array can be empty, though should still be included in the file.

Models that are sold commercially for private use should specify a commercial license, `LicenseRef-Commercial`. SPDX does not have an official built in identifier for this case, so we use the LicenseRef extension mechanism in that standard to define our own. This could be adapted for specific commercial licenses if necessary.

### Example

```json
{
	...
	"licenses": [
		{
			"name": "CC-BY-SA-4.0",
			"path": "https://creativecommons.org/licenses/by-sa/4.0/"
		}
	],
	...
}
```

## Resources

The heart of any 3d model is the model files themselves. The `resources` array lists the files in the package. No particular file or folder structure is required or suggested, whatever paths are used are simply included in the resources array.

Each resource must include a path and a name:

|Field|Description|
|--|--|
|`path`|The filesystem path of the resource (including filename), relative to the datapackage.json file.|
|`name`|A url-safe name for the resource, unique within the data package; e.g. the file base name.|

Resources should also include a media type for the file:

|Field|Description|
|--|--|
`mediatype`|The IANA MIME type for the file, e.g. `model/stl`. In cases where an official MIME type is not available, `x-` prefixes can be used to define custom types. The [supported formats](/manual/supported_formats) page lists the custom types that Manyfold uses for many such files.|

Other fields are defined in the [Data Resource](https://datapackage.org/standard/data-resource/) specification, and can be included if desired. Common ones might include:

|Field|Description|
|--|--|
|`title`|A human-readable title for the file|
|`description`|A human-readable description; can include line breaks and markdown syntax.|
|`bytes`|The file size in bytes|

### Example

```json
{
	...
	"resources": [
		{
			"name": "9-inch-curve",
			"path": "9-inch-curve.stl",
			"mediatype": "model/stl"
		},
		...
	]
	...
}
```

## Contributors and sources

The `contributors` array can be used to link to the creator of a model, and `sources` can be used to link to models that this model was based on (i.e. remix sources), even across different domains. Each should have a title and path, and `contributors` should include a role as well, nominally `creator`.

```json
{
	...
	"sources": [
		{
			"title": "Name of model this was remixed from",
			"path": "https://thingiverse.com/thing:XXXXXXX"
		}
	],
	"contributors": [
		{
			"title": "Floppy",
			"path": "https://manyfold.floppy.org.uk/creators/floppy",
			"roles": ["creator"]
		}
	],
	...
}
```

## JSON Schema Extension

For data that can't be represented in a standard DataPackage, we have defined an extension schema, the "Manyfold 3D Data Package Profile". This is specified in the datapackage.json like so:

```json
{
  "$schema": "https://manyfold.app/profiles/0.0/datapackage.json",
	...
}
```

It adds a number of fields to the format, all of which are optional:

|Field|Description|
|--|--|
|`caption`|A short textual caption|
|`links`|An array of Link objects (see below), for other URLs associated with this model|
|`collections`|An array of collection object (see below)|
|`sensitive`|Boolean value for whether the model as a whole is marked as sensitive (NSFW, explicit content, etc)|

### Resources

Each resource object also gets the following fields:

|Field|Description|
|--|--|
|`caption`|A short textual caption|
|`description`|A longer description of the file; can include Markdown|
|`presupported`|Boolean, whether the 3D object includes supports for printing|
|`up`|A string which specifies the "up" direction for the model, such as "+z" or "+y"|

### Contributor

To represent additional information for creators, we add some fields to the elements in the `contributors` array:

|Field|Description|
|--|--|
|`caption`|A short textual caption|
|`description`|A longer description of the creator; can include Markdown|
|`links`|An array of Link objects (see below), for other URLs associated with this creator|

### Collection

Collection is a new object type, similar to contributor records, which reference a collection object that the object belongs to.

|Field|Description|
|--|--|
|`title`|A human-readable name for the collection|
|`path`|A canonical URL for the collection, similar to `path` in the contributor object.|
|`caption`|A short textual caption|
|`description`|A longer description of the creator; can include Markdown|
|`links`|An array of Link objects (see below), for other URLs associated with this collection|

### Link

Link is another new object type, which simply represents other URLs associated with an item.

|Field|Description|
|--|--|
|`path`|The URL for the related remote resource.|

## Evolution of this specification

This proposal is intended as a minimum standard, and currently consists of only the core Data Package fields. In time, it's likely that extensions will be added to support extra metadata, such as suggested print parameters. Suggestions for extensions are invited from specification implementers via [GitHub issues](https://github.com/manyfold3d/website/issues/new?template=feature_request.md).

## Complete example

```json
{
	"$schema": "https://manyfold.app/profiles/0.0/datapackage.json",
	"name": "40k-deployment-zone-markers",
	"title": "40k Deployment Zone Markers",
	"description": "A set of boundary markers that you can use for deployment zones in 40k games. There's one straight piece which is fairly obvious; then the other two are for curved deployment zones. The curved pieces have the right outside curvature for a 9” circular deployment from the centre.\n\nPrinting four corners, four curves and maybe twelve straights will be enough for a two deployment zones - maybe try two different colours!",
	"homepage": "https://manyfold.floppy.org.uk/models/pkq8x0h7",
	"image": "markers.png",
	"keywords": [
		"40k",
		"deployment",
		"markers"
	],
	"licenses": [
		{
			"name": "CC-BY-SA-4.0",
			"path": "https://creativecommons.org/licenses/by-sa/4.0/"
		}
	],
	"resources": [
		{
			"name": "9-inch-curve",
			"path": "9-inch-curve.stl",
			"title": "9 Inch Curve",
			"mediatype": "model/stl"
		},
		{
			"name": "corner-curve",
			"path": "corner-curve.stl",
			"title": "Corner Curve",
			"mediatype": "model/stl"
		},
		{
			"name": "straight",
			"path": "straight.stl",
			"title": "Straight",
			"mediatype": "model/stl"
		},
		{
			"name": "markers",
			"path": "markers.png",
			"title": "Markers",
			"mediatype": "image/png"
		}
	],
	"contributors": [
		{
			"title": "Floppy",
			"path": "https://manyfold.floppy.org.uk/creators/floppy",
			"roles": [
				"creator"
			]
		}
	]
}
```
