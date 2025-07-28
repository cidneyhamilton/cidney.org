---
layout: page
title: Blog
---

This is an informal collection of things I've written here over the years. All mistakes are mine.

### 2025
{% assign articles = site.posts | where_exp:"item", "item.title.size > 0" %}

<ul>
	{% for post in articles %}
	{% capture year %}{{ post.date | date: "%Y"}}{% endcapture %}
	{% if year == "2025" %}
	<li><a href="{{ post.url }}">{{ post.title}}</a> - {{ post.date | date: "%B %d, %Y" }}</li>
	{% endif %}
	{% endfor %}
</ul>

### 2024
{% assign articles = site.posts | where_exp:"item", "item.title.size > 0" %}

<ul>
	{% for post in articles %}
	{% capture year %}{{ post.date | date: "%Y"}}{% endcapture %}
	{% if year == "2024" %}
	<li><a href="{{ post.url }}">{{ post.title}}</a> - {{ post.date | date: "%B %d, %Y" }}</li>
	{% endif %}
	{% endfor %}
</ul>

### 2023

<ul>
{% for post in articles %}
  {% capture year %}{{post.date | date: "%Y"}}{% endcapture %}
  {% if year == "2023" %}
	  <li><a href="{{ post.url }}">{{ post.title}}</a> - {{ post.date | date: "%B %d, %Y" }}</li>
	{% endif %}
{% endfor %}
</ul>


### 2019-2022

<ul>
{% for post in articles %}
  {% capture year %}{{post.date | date: "%Y"}}{% endcapture %}
  {% if year == "2022" or year == "2021" or year == "2019" %}
	  <li><a href="{{ post.url }}">{{ post.title}}</a> - {{ post.date | date: "%B %d, %Y" }}</li>
	{% endif %}
{% endfor %}
</ul>

