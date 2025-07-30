---
title: News
layout: page
nav_order: 4
---
{% for post in site.posts %}

## [{{ post.title }}]({{ post.url }})

{{ post.excerpt }}
_posted on [{{ post.date | date_to_string }}]({{ post.url }})_

{% endfor %}
