---
title: "Tech"
layout: archive
permalink: /categories/tech/
author_profile: false
sidebar_main: true
entries_layout: grid
---

{% assign posts = site.categories.tech 
  | sort: "date" 
  | reverse %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
