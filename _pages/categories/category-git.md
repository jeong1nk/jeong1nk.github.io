---
title: "git"
layout: archive
permalink: study/git
author_profile: true
sidebar_main: true
types: posts
sidebar:
  nav: "sidebar-category"
  enabled: true
---

{% assign posts = site.categories['git']%}
{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
