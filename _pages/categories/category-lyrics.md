---
title: "Lyrics"
layout: archive
permalink: /categories/lyrics/
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.lyrics %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}