---
title: ActivityPub
parent: Technology
layout: page
nav_order: 1
---

{:.note}
Manyfold's ActivityPub implementation is still evolving, and this document may be inaccurate compared to the latest code, or may include sections that are not yet implemented.


Manyfold instances use the [ActivityPub](http://activitypub.rocks/) protocol to exchange user activity with other instances, and other ActivityPub services, such as [Mastodon](https://joinmastodon.org/).

On top of the ActivityPub standard object types, we define an extension specifically for 3D content, and provide alternatives for use when communicating to instances that don't support it.

## NodeInfo

Manyfold supports the [NodeInfo](https://nodeinfo.diaspora.software/) standard for exposing server capabilities.

Support for extension types will be indicated in the `metadata` field of the nodeinfo response. Several metadata fields are [known](https://codeberg.org/thefederationinfo/nodeinfo_metadata_survey), but we define a new one specifically to indicate 3d model support.

```json
{
  "version": "2.1",
  "software": {
    "name": "manyfold",
    "version": "x.y.z"
  },
  "protocols": [
    "activitypub"
  ],
  "usage": {...},
  "openRegistrations": true|false,
  "metadata": {
    "activitypub": {
      "extensions": [
        "https://w3id.org/activity-streams/extensions/3dModel#v1.0"
      ]
    }
  }
}
```

Platforms such as Pixelfed and Bookwyrm use the `software` field to determine support for their custom types, but as we explicitly want to encourage other implementations, using a structure in `metadata` seems more sensible. We define an [IRI](https://codeberg.org/fediverse/fep/src/branch/main/fep/888d/fep-888d.md) for the extension type, as proposed in [FEP-6481](https://codeberg.org/fediverse/fep/src/branch/main/fep/6481/fep-6481.md).

## Objects

### 3DModel

`3DModel` is a custom ActivityStreams object type, parallel to the similar `Audio` and `Video` types, and consistent with the schema.org [3DModel](https://schema.org/3DModel) type.

This object type corresponds to Manyfold's internal `Model` class. It extends the `Document` core object type, in the same way as `Audio` [in the core spec](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-audio).

The standard ActivityStreams activity types will be used in direct correspondence to events in Manyfold. A new `Model` will results in a `Create` activity, changes will result in `Update` activities, and so on.

If available, the `preview` property of the object includes a URL for both an image and a 3d model file for direct loading by the client, with the appropriate MIME types. Of course, it's up to the client whether it chooses to display these.

### Note

`Note` is used to represent comments on a model; these could either be local to Manyfold, or remote on a different system such as Mastodon.

Servers such as Mastodon that do not support the `3DModel` object type (potentially determined using NodeInfo, above) are sent a `Note` instead, containing a textual description of the event and the canonical URL of the model's web page; the 3D preview will not be included. A new `Note` is created for each event, whether creation, update, etc.

## Actors

Manyfold provides individual ActivityPub actors for the following:

|Manyfold class|ActvityPub actor type|Notes|
|-|-|-|
|User|`Person`||
|Creator|`Person`||
|Collection|`Group`||
|Model|`Service`|used instead of the more accurate `Document` for wider compatibility|

Any of these can be followed via ActivityPub *if they are publicly visible to logged-out users*.

## Activities

The following activities are supported on the object types shown in the table. In summary:

* Following is supported for users, creators, individual models, and collections;
* Standard microblog-interaction-type activities (create, like, boost) are supported for models and comments;
* Collection-oriented activities are supported for users, models, and other collections.

|Activity|Description|object|target|origin|
|-|-|-|-|-|
|`Create`|Actor has published a new model or comment|`3DModel`, `Note`|||
|`Update`|Actor has updated the object (including individual files, in the case of a model)|`3DModel`|||
|`Delete`|Actor has deleted the object|`3DModel`||
|`Flag`|Actor has flagged the object for moderator attention|`3DModel`, `Note`|
|`Follow`|Actor has followed the object to get updates|`Person`, `Group`, `Service`|||
|`Add`|Actor has added the object to the target collection|`3DModel`, `Group`|`Group`||
|`Remove`|Actor has removed the object from the target collection|`3DModel`, `Group`||`Group`|

## Technical implementation

Manyfold's ActivityPub support will be built using the [federails](https://gitlab.com/experimentslabs/federails) Ruby gem.

{:.info}
Many thanks to [Bookwyrm](https://docs.joinbookwyrm.com/activitypub.html) and [Pixelfed](https://docs.pixelfed.org/spec/ActivityPub.html) for their excellent ActivityPub implementation docs, which this page is heavily based on.
