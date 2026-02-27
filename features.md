---
title: Features
layout: page
nav_order: 1
---

Manyfold is under continuous development - there's a lot it can already do, but there's a lot more to come. Why not <a href="/donate">support us</a> to help make all this a reality?

## Now
<div class="feature-list" id="now">
	{% for feature in site.data.features.now %}
		<div>
			<div>
				<div class="when">✔ Available now</div>
				<strong>{{ feature.name }}</strong>
			</div>
			<p>{{ feature.description }}</p>
		</div>
	{% endfor %}
</div>

## Next
<div class="feature-list" id="next">
	{% for feature in site.data.features.next %}
		<div>
			<div>
				<div class="when">⧗ {{ feature.when }}</div>
				<strong>{{ feature.name }}</strong>
			</div>
			<p>{{ feature.description }}</p>
			{% if feature.link %}
				<div class="discussion-link">
					💬 <a href="{{feature.link}}">Discuss on GitHub</a>
				</div>
			{% endif %}
		</div>
	{% endfor %}
</div>

## Later
<div class="feature-list" id="later">
	{% for feature in site.data.features.later %}
		<div>
			<div>
				<div class="when">⏲ {{ feature.when }}</div>
				<strong>{{ feature.name }}</strong>
			</div>
			<p>{{ feature.description }}</p>
			{% if feature.link %}
				<div class="discussion-link">
					💬 <a href="{{feature.link}}">Discuss on GitHub</a>
				</div>
			{% endif %}
		</div>
	{% endfor %}
</div>

<p><small>
Note that all dates are estimates and may change wildly! Roadmap design inspired by <a href="https://joinloops.org/roadmap">Loops</a>
</small></p>
