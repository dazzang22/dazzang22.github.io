---
title: "Unreal"
layout: archive
permalink: /categories/unreal/
author_profile: false
sidebar_main: true
entries_layout: grid
---

{% assign posts = site.categories.unreal
  | where_exp: "p", "p.categories contains 'tech'"
  | sort: "date"
  | reverse %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
