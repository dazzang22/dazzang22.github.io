---
title: "Diary"
layout: archive
permalink: /categories/diary/
author_profile: true
sidebar_main: true
entries_layout: list
---

{% assign posts = site.categories.diary
  | where_exp: "p", "p.categories contains 'life'"
  | sort: "date" | reverse %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
