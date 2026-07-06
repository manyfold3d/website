---
title: Plugins
layout: page
nav_order: 5
---

Plugins are optional extensions which add additional functionality to your Manyfold instance. Plugins can add elements to the user interface, add additional file types or API connections, and a lot more!

For information on how to configure your instance to run plugins, see the [admin guide](/sysadmin/plugins), and to write your own, check out the [developer guide](/technology/plugins).

## Available Plugins

<table>
	<tr>
		<th>Name</th>
		<th>Summary</th>
		<th>Version</th>
		<th>Released</th>
		<th></th>
	</tr>
	{% for plugin in site.data.plugins %}
		<tr id="{{ plugin[0] }}">
			<td>
				<a href="{{ plugin[1].download_link }}" download>
					{{ plugin[1].name }}
				</a>
			</td>
			<td>{{ plugin[1].summary }}</td>
			<td>{{ plugin[1].version }}</td>
			<td>{{ plugin[1].release_date }}</td>
			<td>
				<a href="{{ plugin[1].download_link }}" title="Download" download>
					<img src="/images/cloud-download.svg" role="presentation">
				</a>
				<a href="{{ plugin[1].source_link }}" title="Source code">
					<img src="/images/file-earmark-code.svg" role="presentation">
				</a>
			</td>
		</tr>
	{% endfor %}
</table>
{:.note}
Plugins are a very new feature! We hope to see many more plugins soon! Why not try [writing your own](/technology/plugins)? Or, you might find more using the [manyfold-plugin](https://github.com/topics/manyfold-plugin) topic on GitHub!
