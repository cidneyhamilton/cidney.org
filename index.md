---
layout: home
heading: start
---

{% include hcard.html %}

### Latest Posts

<ul>
	{% assign articles = site.posts | where_exp:"item", "item.title.size > 0" %}
  {% for post in articles limit:5 %}
  <li>
    <a href="{{ post.url }}">{{ post.title}}</a> - {{ post.date | date: "%B %d, %Y" }}
  </li>
  {% endfor %}
</ul>

<a href="/blog">View more &rarr;</a>