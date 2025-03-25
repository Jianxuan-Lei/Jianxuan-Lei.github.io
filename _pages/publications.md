---
layout: archive
title: "Research"
permalink: /research/
header:
  overlay_image: xihu1.jpg
  overlay_filter: 0.1
author_profile: true
---

## Work in Progress

{% assign wip = site.publications | where: "status", "in-progress" | sort: "year" | reverse %}
{% for post in wip %}
  {% include archive-single2.html %}
{% endfor %}

---

## Published Work

{% assign published = site.publications | where: "status", "published" | sort: "year" | reverse %}
{% for post in published %}
  {% include archive-single2.html %}
{% endfor %}
