---
title: "Algorithm"
layout: archive
permalink: /categories/algorithm/
author_profile: false
sidebar_main: true
entries_layout: grid   # "list"도 가능
---

{% assign posts = site.categories.algorithm
  | where_exp: "p", "p.categories contains 'tech'"
  | sort: "date"
  | reverse %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}