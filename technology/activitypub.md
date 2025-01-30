---
title: ActivityPub
parent: Technology
layout: page
nav_order: 1
---

Manyfold instances use the [ActivityPub](http://activitypub.rocks/) protocol to exchange user activity with other instances, and other ActivityPub services, such as [Mastodon](https://joinmastodon.org/). We use ActivityPub standard object types to directly federate content, and also post activities as Notes for use by microblog-style instances (e.g. Mastodon).

## ActivityPub extensions

Manyfold uses the following extensions in its ActivityPub messages, specified in the JSON-LD `@context`:

|Namespace|URI|Notes|
|-|-|-|
|`as`|https://www.w3.org/ns/activitystreams|used for [hashtags](https://swicg.github.io/miscellany/#Hashtag) and [sensitive]https://swicg.github.io/miscellany/#sensitive).
|`f3di`|http://purl.org/f3di/ns#|a custom namespace for federation of 3d content; see next section for details.
|`sec`|https://w3id.org/security/v1|used for public keys.
|`spdx`|http://spdx.org/rdf/terms#|used to specify license information.
|`toot`|http://joinmastodon.org/ns#|used for [attributionDomains](https://blog.joinmastodon.org/2024/07/highlighting-journalism-on-mastodon/).

### JSON-LD `f3di` namespace

In order to support 3d content over ActivityPub, we extend the vocabulary to support required concepts. The namespace is called `f3di` instead of a more application-specific one like `manyfold`, because we hope that other platforms will also adopt and help shape this specification to federate 3d content.

#### f3di:concreteType

In ActivityPub, an [Actor](https://www.w3.org/TR/activitypub/#actors) is (basically) any [Object](https://www.w3.org/TR/activitypub/#obj) that can perform an activity, and which has an inbox and outbox. In theory, Actors can have any `type`; they could be any defined object type, or a custom one. However, in practice, some Fediverse software only handles messages from certain types of Actor. Specifically, Mastodon (the dominant platform at present) only supports a limited set of Actors. Because of this, for compatibility, we choose to use Actor types from this limited subset.

However, we still need to know exactly what type of object is being represented, so `concreteType` is used to distingish between domain-specific types at a finer level of detail than Actor type allows. It also allows us to detect whether the remote Actor is a type relevant to Manyfold.

For examples, see the actor documentation below.

#### f3di:compatibilityNote

A boolean flag to indicate if a Note is posted for compatibility reasons. See the [Notes](#Notes) section below for details.

## Actors

Manyfold exposes the following ActivityPub actors, any of which can be discovered and followed *if they are publicly visible to logged-out users*.

|ActivityPub actor type|f3di:concreteType|Manyfold class|Description|
|-|-|-|-|
|`Service`|`3DModel`|Model|A 3d model (a coherent set of files and metadata)|
|`Person`|`Creator`|Creator|An entity (individual or organisation) that publishes models|
|`Group`|`Collection`|Collection|A collection of models|
|`Person`|`User`|User|A login account on a Manyfold instance; not necessarily a Creator|

Using a combination of the Actor type and the concreteType, a remote Manyfold-compatible Actor can be identified and mapped to the appropriate domain-specific class.

### Model

A 3D model, which in Manyfold terms is a collection of one or more 3d files that are intended to be used together, along with associated metadata.

|Property|Data type|Description|Manyfold database field|Example|Note|
|-|-|-|-|-|-|
|`type`|string|Actor type||always `"Service"`||
|`f3di:concreteType`|string|Domain-specific type||always `"3DModel"`||
|`name`|string|Display name|`name`|`"Tablet Stand"`||
|`preferredUsername`|string|Fediverse account username|`username`|`"fjtcb1xl"`|Manyfold randomly generates these for models at present|
|`summary`|string|Short-form textual description; allows HTML|caption||Manyfold creates HTML from Markdown. Appears as bio on Mastodon.|
|`content`|string|Longer-form description; allows HTML|notes||Manyfold creates HTML from Markdown. Not shown on Mastodon.|
|`attachment`|object[]|standard ActivityStreams [attachment](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-attachment)|links|<code>[<br>&nbsp;{<br>&nbsp;&nbsp;"type":&nbsp;"Link",<br>&nbsp;&nbsp;"href":&nbsp;"https://example.com"<br>&nbsp;}<br>]</code>|Manyfold only creates and parses `Link` attachments at present|
|`as:sensitive`|boolean|Used to [indicate sensitive content](https://swicg.github.io/miscellany/#sensitive) that some viewers may wish to hide by default.|sensitive|`true`||
|`as:tag`|[Hashtag](https://swicg.github.io/miscellany/#Hashtag)[]||tags|<code>[<br>&nbsp;{<br>&nbsp;&nbsp;"type":&nbsp;"Hashtag",<br>&nbsp;&nbsp;"href":&nbsp;"...",<br>&nbsp;&nbsp;"name":&nbsp;"#Household"<br>&nbsp;}<br>]</code>|Manyfold attempts to turn multiword tags into CamelCase, for accessibility.|
|`attributedTo`|id|A link to an actor for the model creator, if available|creator|||
|`context`|id|A link to an actor for a collection that contains the model, if any|collection|||
|`spdx:license`|[License](https://spdx.org/rdf/terms/#d4e2638)|A license definition from [SPDX](https://spdx.org/licenses/)||<code>{<br>&nbsp;"@id":&nbsp;"http://spdx.org/licenses/CC-BY-SA-4.0",<br>&nbsp;"spdx:licenseId":&nbsp;"CC-BY-SA-4.0"<br>}</code>|Manyfold uses `LicenseRef-Commercial` to identify paid-for models; this isn't a proper SPDX license, so won't have the `@id` property.|

Standard Actor [properties](https://www.w3.org/ns/activitystreams#activitypub) (e.g. `inbox`) are also included and use the standard semantics.

### Creator

An entity which creates and publishes models; i.e. a content creator or author. Not necessarily related to an actual individual or user of an instance.

|Property|Data type|Description|Manyfold database field|Example|Note|
|-|-|-|-|-|-|
|`type`|string|Actor type||always `"Person"`||
|`f3di:concreteType`|string|Domain-specific type||always `"Creator"`||
|`name`|string|Display name|`name`|`"Floppy"`||
|`preferredUsername`|string|Fediverse account username|`username`|`"floppy"`||
|`summary`|string|Short-form textual description; allows HTML|caption||Manyfold creates HTML from Markdown. Appears as bio on Mastodon.|
|`content`|string|Longer-form description; allows HTML|notes||Manyfold creates HTML from Markdown. Not shown on Mastodon.|
|`attachment`|object[]|standard ActivityStreams [attachment](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-attachment)|links|<code>[<br>&nbsp;{<br>&nbsp;&nbsp;"type":&nbsp;"Link",<br>&nbsp;&nbsp;"href":&nbsp;"https://example.com"<br>&nbsp;}<br>]</code>|Manyfold only creates and parses `Link` attachments at present|
|`toot:attributionDomains`|string[]|A list of domains that are valid for `fediverse:creator` [opengraph tags](https://blog.joinmastodon.org/2024/07/highlighting-journalism-on-mastodon/)||`["try.manyfold.app"]`|Will always be set to the account domain|

Standard Actor [properties](https://www.w3.org/ns/activitystreams#activitypub) (e.g. `inbox`) are also included and use the standard semantics.

### Collection

A collection of models.

|Property|Data type|Description|Manyfold database field|Example|Note|
|-|-|-|-|-|-|
|`type`|string|Actor type||always `"Group"`||
|`f3di:concreteType`|string|Domain-specific type||always `"Collection"`||
|`name`|string|Display name|`name`|`"Household items"`||
|`preferredUsername`|string|Fediverse account username|`username`|`"fjtcb1xl"`|Manyfold randomly generates these at present|
|`summary`|string|Short-form textual description; allows HTML|caption||Manyfold creates HTML from Markdown. Appears as bio on Mastodon.|
|`content`|string|Longer-form description; allows HTML|notes||Manyfold creates HTML from Markdown. Not shown on Mastodon.|
|`attachment`|object[]|standard ActivityStreams [attachment](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-attachment)|links|<code>[<br>&nbsp;{<br>&nbsp;&nbsp;"type":&nbsp;"Link",<br>&nbsp;&nbsp;"href":&nbsp;"https://example.com"<br>&nbsp;}<br>]</code>|Manyfold only creates and parses `Link` attachments at present|

Standard Actor [properties](https://www.w3.org/ns/activitystreams#activitypub) (e.g. `inbox`) are also included and use the standard semantics.

### User

An individual user account. These will follow the above actors, but in general, they're not currently expected to be followed by others.

|Property|Data type|Description|Manyfold database field|Example|Note|
|-|-|-|-|-|-|
|`type`|string|Actor type||always `"Person"`||
|`f3di:concreteType`|string|Domain-specific type||always `"User"`||
|`name`|string|Display name|`name`|`"James"`||
|`preferredUsername`|string|Fediverse account username|`username`|`"fjtcb1xl"`|Manyfold randomly generates these at present|

Standard Actor [properties](https://www.w3.org/ns/activitystreams#activitypub) (e.g. `inbox`) are also included and use the standard semantics.

## Activities

Manyfold will post and receive activities as follows.

|Actor/concreteType|Create|Update|Delete|Flag|Follow|Accept|Undo|
|-|-|-|-|-|-|-|-|
|`Service/3DModel`|both|both|both|receive|receive|send|receive|
|`Person/Creator`|both|both|both|receive|receive|send|receive|
|`Group/Collection`|both|both|both|receive|receive|send|receive|
|`Person/User`||||both|send|receive|send|
|`Note` (see below)|send|send|send|receive|||||

### Notes

Much of Manyfold's activity is based around actions that are happening to the Actors themselves; for instance
"This Creator has been updated". However, in a microblog-style application, this would not be visible, or at best would
just appear as a change in the profile information. Therefore, for compatibility with microblog-style services, Manyfold
also posts `Note` objects, just as an application such as Mastodon would.

These notes contain a textual summary of what an activity, which can be displayed in lieu of the actual activity itself.
For instance, in the scenario where a new Model is added by a particular Creator:

1. The creator posts a `Create` activity, where the object is the new `Service/3DModel`. It will be posted to the creator's
   followers, and Manyfold (and compatible) instances can respond can create their own Model object with the received information.
2. The creator also posts a `Create` activity with a `Note` object. The note contains a text description of the change, in this case
   announcing that a new model has been posted, including a link to the model and other microblog compatible data. Manyfold instances
   will ignore this note, as they are getting the "real" create activity, but other Fediverse platforms will receive and display it in
   users timelines. These notes are posted with a `f3di:compatibilityNote` property set to `true`, so they can be ignored by platforms that
   don't need them.

Note that by default, this means that each change will be posted twice to all followers. An instance may use NodeInfo extension data (see below)
to determine which activities and actors a remote server supports, and only send the appropriate activity. Manyfold has not yet implemented this
filtering, but will do soon.

## NodeInfo

Manyfold supports the [NodeInfo](https://nodeinfo.diaspora.software/) standard for exposing server capabilities.

{:.note}
The following information is proposed, and not yet implemented by Manyfold.

Support for extension types is indicated in the `operations` field of the nodeinfo response following the
method proposed in [FEP-9fde](https://codeberg.org/fediverse/fep/src/branch/main/fep/9fde/fep-9fde.md)

Currently `f3di.accept.3dmodel` is proposed as the extension name, though this is subject to change as the FEP and
behaviour evolves.

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
  "operations": {
    "f3di.accept.3dmodel": ["0.1.0"]
  }
}
```

## Technical implementation

Manyfold's ActivityPub support is built using the [Federails](https://gitlab.com/experimentslabs/federails) Ruby gem, which is a reusable
Rails engine for adding ActivityPub support to existing Rails apps.

{:.info}
Many thanks to [Bookwyrm](https://docs.joinbookwyrm.com/activitypub.html) and [Pixelfed](https://docs.pixelfed.org/spec/ActivityPub.html) for their excellent ActivityPub implementation docs, which this page is heavily based on.
