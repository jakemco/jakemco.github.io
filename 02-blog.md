---
layout: default
title: Blog
group: "navigation"
permalink: /blog/
is_blog: true
---

{% for post in site.posts %}
  <h1><a href="{{ post.url }}" style="color: black">{{ post.title }}</a> <small>{{post.subtitle}}</small></h1>
  <h5>{{ post.date | date: '%B %d, %Y' }}</h5>
  <div class="post">
  {{ post.excerpt }}
  </div>
  <a href="{{post.url}}">Read More...</a>
{% endfor %}
