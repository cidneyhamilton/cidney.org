---
layout: home
heading: start
---

{% include hcard.html %}

### Latest Posts

<ul>
  {% for post in site.posts limit:5 %}
  <li>
    <a href="{{ post.url }}">{{ post.title}}</a> - {{ post.date | date: "%B %d, %Y" }}
  </li>
  {% endfor %}
</ul>

<a href="/blog">View more &rarr;</a>