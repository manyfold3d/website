---
title: Adding a Library
parent: Get Started
layout: page
nav_order: 3
---

Now you're logged in and secure, you can set up your first library. In Manyfold, a "Library" is a collection of files stored _somewhere_. You will probably only have one library, but you might have more (which could even be on different storage systems); it's up to you how you want to organise your storage.

You can create a library in either:

* [a folder on your local filesystem](#local-filesystem)
* [cloud storage using any S3-compatible provider](#cloud-storage-with-s3)

In both cases, Manyfold will organise and name the files and folders in your library storage for you. It will also scan and index any files that are in that location that it doesn't know about.

![Folder structure](/images/get-started/folders.png){:.screenshot}

So, if you have an existing big folder of models, you set it up as a library and Manyfold will take care of it from there. Or, you can create a library in an empty folder and upload everything through the website.

You can add more libraries later on, but you need to add at least one before Manyfold can operate properly.

## Local filesystem

When setting up a local folder as a library, you need to have mounted the folder as a bind mount in the Manyfold Docker container. The earlier installation documents recommend that you mount folders in /libraries, but you can use any path you like.

![Library setup page for local filesystem](/images/get-started/local-filesystem.png){:.screenshot}

When setting the library path, note that you need to use the path _inside the container_, not on your host server.

For example, let's say you have a folder called `~/models/` with folders called `tabletop` and `misc` inside it that are full of models, and you want to treat each one as a separate library. In your docker container setup, you would maps `~/models` to `/libraries` inside the container.

Then the `tabletop` and `misc` folders would be visible inside the container at `/libraries/tabletop` and `/libraries/misc`; these are the paths you'd put into the library form.

## Cloud storage with S3

If you want to use cloud storage for infinitely-expandable space, you can use one of a huge number of S3-compatible
storage providers. There are lots out there, both [open source and self hosted](https://github.com/okhosting/awesome-storage?tab=readme-ov-file#s3-compatible-file-servers), or [commercial](https://www.storageprovider.info/blog/all-s3-storage-providers/).

![S3 cloud storage setup](/images/get-started/s3.png){:.screenshot}

To set up S3 storage, select it from the Storage Service dropdown, and enter your bucket name, region, and access keys.

Note that Manyfold will treat the entire bucket as its library, so don't use one that you're already using for something else!

If you're using a non-Amazon S3 provider, you will need to set the endpoint URL, and you may not need to specify a particular region; refer
to your provider's documentation for the details.
