---
title: "tinlab - Research"
layout: gridlay
excerpt: "tinlab -- Research"
sitemap: false
permalink: /research/
---

<style>
  .author-list {
    color: #444;
  }
  /* Visually appealing highlight for tinlab members */
  .author-list strong, .author-list b {
    font-weight: 600;
    border-bottom: 2px solid #f472b6
  }
  /* Venue badge */
  .pub-venue {
    display: inline-block;
    font-size: 0.82em;
    font-weight: 600;
    color: #0f5151;
    background-color: #e6f7f7;
    border: 1px solid #029696;
    border-radius: 4px;
    padding: 1px 7px;
    vertical-align: middle;
    margin-top: 6px;
  }
  /* Award badge */
  .pub-award {
    display: inline-block;
    font-size: 0.82em;
    font-weight: 600;
    color: #92400e;
    background-color: #fef3c7;
    border: 1px solid #f59e0b;
    border-radius: 4px;
    padding: 1px 7px;
    margin-left: 4px;
    vertical-align: middle;
    margin-top: 6px;
  }
</style>

# Research

Publications and presentations from tinlab are listed below. Lab members are highlighted.

{% for publi in site.data.publist %}

  <a href="{{ publi.url }}">{{ publi.title }}</a> <br />
  <span class="author-list">{{ publi.authors | markdownify | remove: '<p>' | remove: '</p>' | strip_newlines }}</span> <br />
  <span class="pub-venue">{{ publi.venue }}</span>{% if publi.award %} <span class="pub-award">👑 {{ publi.award }}</span>{% endif %} <br />
  <hr style="margin-top: 10px; margin-bottom: 20px; border-top: 1px solid #ccc;"/>

{% endfor %}
