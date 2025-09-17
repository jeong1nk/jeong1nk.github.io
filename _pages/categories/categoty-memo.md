---
title: "기록: 개인적인 기록 공간"
layout: archive
permalink: /etc/memo
author_profile: true
sidebar_main: true
types: posts
sidebar:
  nav: "sidebar-category"
  enabled: true
---


설명입니다.

{% assign posts = site.categories.memo %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}