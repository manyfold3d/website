---
title: ActivityPub
parent: Technology
layout: page
nav_order: 1
---

{:.important}
Manyfold does not yet include ActivityPub federation, or even multiuser support. This document is a proposal for comment, which explores how Manyfold instances _might_ interact with the Fediverse in future. Feedback is welcome; please comment on the [GitHub issue](https://github.com/manyfold3d/manyfold/issues/1389) with your thoughts!

Manyfold instances should use the [ActivityPub](http://activitypub.rocks/) protocol to exchange user activity with other instances, and other ActivityPub services, such as [Mastodon](https://joinmastodon.org/).

On top of the ActivityPub standard object types, we define an extension specifically for 3D content, and provide a mapping back to the standard for use when communicating to instances that don't support them.

## NodeInfo

Manyfold will support the [NodeInfo](https://nodeinfo.diaspora.software/) standard for exposing server capabilities.

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
      "extensions": {
        "https://w3id.org/activity-streams/extensions/3dModel": "1.0"
      }
    }
  }
}
```

Platforms such as Pixelfed and Bookwyrm use the `software` field to determine support for their custom types, but as we explicitly want to encourage other implementations, using a structure in `metadata` seems more sensible. We define an [IRI](https://codeberg.org/fediverse/fep/src/branch/main/fep/888d/fep-888d.md) for the extension type, and use a version field rather than boolean, in case of future changes.

## Objects

### 3dModel

`3dModel` is a custom ActivityStreams object type, corresponding to Manyfold's internal `Model` class. It extends the `Document` core object type, in the same way as `Audio` [in the core spec](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-audio).

If available, the `preview` property of the object will include a URL for both an image and a 3d model file for direct loading by the client, with the appropriate MIME types. Of course, it's up to the client whether it chooses to display these.

#### Supported activities

|Activity|Description|Actor|
|-|-|-|
|Create|A new model has been published|model creator|
|Update|The model or its files have been changed|model creator|
|Delete|The model has been removed|model creator|
|Announce|A user "boosts" the model into their own timeline|other user|
|Follow|A user has followed the model to get updates|other user|
|Like|A user has liked the model|other user|

Future expansion may include `Add` and `Remove` activities for collections.

#### Downgrading

Servers that do not support the `3dModel` object type (as determined using NodeInfo, above) will be sent a `Link` instead, containing the canonical URL of the model's web page, and the 3D preview will not be included.

### Actor

Our `Actor` objects are just as defined in the ActivityPub standard; they correspond to our signed-up users, and will use the `Person` type.

{:.note}
Note that Manyfold's internal`Creator` class is not the same thing; Manyfold can store creator metadata even when the creators do not have an account on the instance. Only activities from actual real users of an instance are federated; creators that are purely made for metadata purposes will not be exposed.

### Collection

We anticipate using the standard's `Collection` feature to support activities around users adding models to collections. This will operate using all the standard semantics.

### Note

`Note` is used to represent comments on a model; these could either be local to Manyfold, or remote on a different system such as Mastodon. A Manyfold `Note` will always be in reply to something, either a `3dModel` or another `Note`. They operate in accordance with the standard.

## Technical implementation

Manyfold's ActivityPub support will be built using the [federails](https://gitlab.com/experimentslabs/federails) Ruby gem.

{:.info}
Many thanks to [Bookwyrm](https://docs.joinbookwyrm.com/activitypub.html) and [Pixelfed](https://docs.pixelfed.org/spec/ActivityPub.html) for their excellent ActivityPub implementation docs, which this page is heavily based on.
