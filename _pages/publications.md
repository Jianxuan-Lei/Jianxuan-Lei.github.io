---
layout: archive
title: "Research"
permalink: /research/
header:
  overlay_image: xihu1.jpg
  overlay_filter: 0.1
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}


## Work in Progress

{% assign wip = site.publications | where: "status", "in-progress" | sort: "year" | reverse %}
{% for post in wip %}
  {% include archive-single.html %}
{% endfor %}

---

## Published Work

{% assign published = site.publications | where: "status", "published" | sort: "year" | reverse %}
{% for post in published %}
  {% include archive-single.html %}
{% endfor %}
