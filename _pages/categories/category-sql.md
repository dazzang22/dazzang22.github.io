---
title: "SQL"
layout: archive
permalink: /categories/sql/
author_profile: false
sidebar_main: true
entries_layout: grid
---

{% assign posts = site.categories.sql
  | where_exp: "p", "p.categories contains 'tech'"
  | sort: "date"
  | reverse %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
