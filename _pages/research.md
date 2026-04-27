---
title: "tinlab - Research"
layout: gridlay
excerpt: "tinlab -- Research"
sitemap: false
permalink: /research/
---

# Research

Publications and presentations from tinlab are listed below. Lab members are highlighted.

{% for publi in site.data.publist %}

  <a href="{{ publi.url }}">{{ publi.title }}</a> <br />
  <span class="author-list">{{ publi.authors | markdownify | remove: '<p>' | remove: '</p>' | strip_newlines }}</span> <br />
  <span class="pub-venue">{{ publi.venue }}</span>{% if publi.award %} <span class="pub-award">👑 {{ publi.award }}</span>{% endif %} <br />
  <hr style="margin-top: 10px; margin-bottom: 20px; border-top: 1px solid #ccc;"/>

{% endfor %}

