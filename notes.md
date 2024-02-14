---
layout: page
title: All Notes
---

{% assign notes = site.posts | where_exp:"item", "item.title.size == 0" %}

<ul>
	{% for post in notes %}
	<li>
		<article class="h-entry">
			<div class="post-content e-content p-content">
				{{ post.content}}
			</div>
			<a class="u-bridgy-fed" href="https://fed.brid.gy/" hidden="from-humans"></a>
			<a class="u-url dt-published" href="{{ post.url }}">{{ post.date | date: "%B %d, %Y %H:%M" }}</a>
		</article>
	</li>
	{% endfor %}
</ul>

