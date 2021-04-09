---
layout: default
title: Blog
permalink: /blog/
is_blog: true
---

{% for post in site.posts %}
  {% include post_content %}
{% endfor %}
