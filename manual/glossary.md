---
title: Glossary
parent: User Guide
layout: page
nav_order: 1
---

# Description of terms used in Manyfold

{:.devquote}
_Naming things is hard.  -- James, creator of Manyfold_

## Library

A library is a path to a folder on disk or an S3-compatible bucket. It's used to store, sort, and catalogue models.

Libraries are hidden by default. Administrators can turn on the option to show the libraries in the top menu bar of the UI.

Adminstrators can change settings and see statistics of libraries in **Site Settings** -> **Libraries**.

## Model

A model in Manyfold is a set of files related to a 3D model. As an example, a miniature with printing instructions, images, unsupported and pressupported 3MF files would be one model. A DIY 3D printer is one model. A 3D printed telescope is one model.

When uploading multiple files related to the same model, compressing it into a single file makes it easier for Manyfold to determine that it's a single model.

Models can be edited to have a preview image, description, a license, links and more. Models can be associated with a [Creator](#creator) and be added to a [Collection](#collection).

Models can be followed on the Fediverse.

### Model File

A model file is a single file associated with a model.

Supported formats are listed in the [Supported Formats](/manual/supported_formats) section of the manual. Files may be rendered differently in the UI based on their MIME type. Be sure to check out the linked section for more information.

## Creator

A Creator is a named entity that can be assigned as a Creator of a model. User accounts and Creators are separate.

Creators can have a tagline, description, and links associated with them. This is helpful for pointing to specific project websites where models have been downloaded previously.

Creators can be followed on the Fediverse.

## Collection

A collection is a set of models. Collections can be added to other collections to create a sub-collection.

Collections could be used like categories, like in the following example:
```
-- Household --> Kitchen --> Coffee tools
             │           └-> Tea tools
             └-> Office
-- Game models --> Board
               └-> Card
               └-> Tabletop
```

Collections can also be used to help sort things:
```
-- Publicly shared
-- Private
```

Collections can be followed on the Fediverse.

## Tags

Tags are useful for searching for models across collections and libraries.

Tags can be added when editing a model.
