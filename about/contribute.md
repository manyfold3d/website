---
title: Contribute
parent: About
layout: page
nav_order: 1
---

As a free and open source application, Manyfold is really built by its community. There are lots of ways to get involved if you'd like to help!

<div class="card-list col-1">
	{% for method in site.data.contributions %}
		<div>
			<details>
				<summary>{{ method.name}}</summary>
				<p>{{ method.description }}</p>
				{% if method.wanted %}
					<p><em>Particularly welcome: {{ method.wanted | join: ", " }}</em></p>
				{% endif %}
				<ul>
					{% for link in method.links %}
						<li><a href="{{ link.url }}">{{ link.text }}</a></li>
					{% endfor %}
				</ul>
			</details>
		</div>
	{% endfor %}
