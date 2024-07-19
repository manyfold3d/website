---
title: Installation
parent: Get Started
layout: page
nav_order: 1
---
Manyfold is an open source self-hosted web application, distributed as a [Docker](https://docker.com) container. The container runs a Rails server, which you access through your web browser.

Select a method below for more instructions!

<div class='installation-methods'>
	{% for method in site.installation %}
		<div class='method'>
			<a href='{{method.url}}'>
				<img src='{{method.logo_url}}' alt='{{method.title}}'/>
				<br/>{{method.title}}
			</a>
		</div>
	{% endfor %}
</div>
