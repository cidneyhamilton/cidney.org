---
layout: home
heading: start
---

{% include hcard.html %}

You can find out more about me and what I do [here](/about). The best way to [contact me](/contact) is by [email](mailto:{{ site.email }}).

I write longer stuff here and microblog on <a href="{{
site.fedi-url}}">the fediverse</a>. If you're trying to follow along,
there's <a href="https://cidney.org/feed.xml">an RSS feed</a> and the
occasional crosspost to the fediverse.

### Blog Posts

<ul>
	{% assign articles = site.posts | where_exp:"item", "item.title.size > 0" %}
  {% for post in articles limit:20 %}
  <li>
    <a href="{{ post.url }}">{{ post.title}}</a> - {{ post.date | date: "%B %d, %Y" }}
  </li>
  {% endfor %}
</ul>

<a href="/blog">View more &rarr;</a>