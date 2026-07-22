---
title: Instances
parent: About
layout: page
nav_order: 4
redirect_from:
  - /instances
---
Manyfold instances aren't all public, but some of them are! Here's a few sharing their content publicly. Visit to take a look, or follow on the Fediverse!

{% assign instances = site.data.instances | sort: 'name' %}
|Instance|Federation|Open signups|Notes|
|-|-|-|-|
{% for instance in instances %}|[{{instance.name}}]({{instance.url}})|{{instance.federation}}|{{instance.open_signup}}|{{instance.note}}|
{% endfor %}

If you'd like to add your instance to the list, [get in touch](community.md)!
