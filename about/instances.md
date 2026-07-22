---
title: Instances
parent: About
layout: page
nav_order: 4
redirect_from:
  - /instances
---
Manyfold instances aren't all public, but some of them are! Here's a few sharing their content publicly. Visit to take a look, or follow on the Fediverse!

<table>
  <tr>
    <th>Instance</th>
    <th>Federation</th>
    <th>Open signups</th>
    <th>Notes</th>
  </tr>
  {% assign instances = site.data.instances | sort: 'name' %}
  {% for instance in instances %}
  <tr>
    <td><a href="{{instance.url}}">{{instance.name}}</a></td>
    <td>{% if instance.federation %}✅{% else %}❌{% endif %}</td>
    <td>{% if instance.open_signup %}✅{% else %}❌{% endif %}</td>
    <td>{{instance.note}}</td>
  </tr>
  {% endfor %}
</table>

If you'd like to add your instance to the list, [get in touch](community.md)!
