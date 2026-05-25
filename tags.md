---
title: tags
permalink: /tags/
---

{% assign tags = site.tags | sort %}

<p class="tag-cloud">
{% for tag in tags %}<a class="tag" href="#{{ tag[0] }}">#{{ tag[0] }} <span class="muted">{{ tag[1].size }}</span></a>{% endfor %}
</p>

{% for tag in tags %}
<h2 id="{{ tag[0] }}">#{{ tag[0] }}</h2>
<ul class="post-list">
  {% for post in tag[1] %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
  </li>
  {% endfor %}
</ul>
{% endfor %}
