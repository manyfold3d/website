---
title: Integrations
parent: User Guide
layout: page
nav_order: 4
---

Manyfold (v0.118+) can import and synchronise content and metadata from other hosting sites. That means you can automatically grab correct metadata, images, and (from some sites) 3d files!

<details markdown="block">
  <summary>
    Contents
  </summary>
- TOC
{:toc}
</details>

## Supported Data

We can currently read data from the following sites:

* [Cults3D](https://cults3d.com)
* [MyMiniFactory](https://myminifactory.com)
* [Thingiverse](https://thingiverse.com)

Different sites support different capabilities; the tables below summarises what can be imported from where. Blank cells indicate the site doesn't have the relevant feature, and the hourglass icon (⏳) indicates something we hope to add in future.

<details markdown="block">
  <summary>
    Models
  </summary>

|Site|Name, Description, Tags|Images|Public Files|Private Files|Sensitive|License|Creator|
|--|--|--|--|--|--|--|--|--|
|Cults3d|✅|✅|❌|❌|✅|✅|✅|
|MyMiniFactory|✅|✅|⏳|⏳|||✅|
|Thingiverse|✅|✅|✅||✅|⏳|✅|

</details>

<details markdown="block">
  <summary>
    Creators
  </summary>

|Site|Name|Description|
|--|--|--|
|Cults3d|✅|✅|
|MyMiniFactory|✅|✅|
|Thingiverse|✅|✅|

</details>

<details markdown="block">
  <summary>
    Collections
  </summary>

|Site|Name|Description|Creator|Models|
|--|--|--|--|--|
|Cults3d|||||
|MyMiniFactory|✅||✅|✅|
|Thingiverse|✅|✅|✅|✅|

</details>

More sites and features will be added over time as we implement them, and as APIs become available. If you know a particular request we should look at, file a [feature request](https://github.com/manyfold3d/manyfold/issues/new?template=feature_request.md)!

## Configuration

Most integrations require some sort of authentication in order for Manyfold to communicate and download data. In the settings area, there is an Integrations page, where you can enter the API keys for each site.

![Integration settings](/images/manual/integration-settings.png){:.screenshot}

 Note that these are all site-wide settings currently; in future, if we are able to synchronise private content from some sites, there will likely be user-level settings as well.

## Links & Synchronisation

Synchronisation is handled via item links; if you add a link to an object, and if the site is supported and configured, you will see a sync icon next to the link on the item page.

![Sync icon next to link](/images/manual/integration-sync.png){:.screenshot}

Clicking that icon will run a synchronisation with the remote content, and over the next few seconds, the item should update itself. Currently, synchronisation is manually triggered (automation and scheduling will be implemented in the future).

## Direct Import

Another integration feature is the ability to directly import a model (or other item) from just a URL from a supported and configured site.

To import an item, simply copy the appropriate page URL from the hosting site, and paste it into the Manyfold search box.

![Enter a URL into the search box](/images/manual/integration-import-search.png){:.screenshot}

If the URL already exists on a local item, you will be sent to the local copy, but if not, and the URL is compatible, you will be presented with a page describing what can be imported, and what type of object Manyfold thinks it is.

![Import confirmation](/images/manual/integration-import-confirm.png){:.screenshot}

When you confirm the import, the process will start, and after a few seconds, the remote item should appear in your local library!

![Imported model page](/images/manual/integration-import-success.png){:.screenshot}
