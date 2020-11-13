---
title: Home
layout: base
---

{% for post in site.posts %}
<div class="blog-post">
<a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a>
<h5><i class="fas fa-calendar-alt"></i>{{ post.date }}<h5>
</div>
{% endfor -%}

