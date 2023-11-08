---
layout: home
heading: start
---

Hi, I'm Cidney, and this is my personal website.

I'm a programmer and designing specializing in [telling stories](/games) through [interactive media](/uses).

### Latest Entries

<ul>
  {% for post in site.posts limit:5 %}
  <li>
    <a href="{{ post.url }}">{{ post.title}}</a> - {{ post.date | date: "%B %d, %Y" }}
  </li>
  {% endfor %}
</ul>

<a href="/blog">View more &rarr;</a>