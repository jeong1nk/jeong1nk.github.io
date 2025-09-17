---
title: "html"
layout: archive
permalink: study/html
author_profile: true
sidebar_main: true
types: posts
sidebar:
  nav: "sidebar-category"
  enabled: true
---

{% assign posts = site.categories['html']%}
{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
