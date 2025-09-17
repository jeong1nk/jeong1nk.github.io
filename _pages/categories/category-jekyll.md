---
title: "jekyll"
layout: archive
permalink: /study/jekyll
author_profile: true
sidebar_main: true
types: posts
# taxonomy:
sidebar:
  nav: "sidebar-category"
  enabled: true
---

{% assign posts = site.categories['jekyll']%}
{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
