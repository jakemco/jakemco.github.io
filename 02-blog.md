---
layout: default
title: Blog
group: "navigation"
permalink: /blog/
is_blog: true
---

{% for post in site.posts %}
  {% include post_content %}
{% endfor %}
