---
title: "tinlab - Invited Speaker Series"
layout: textlay
excerpt: "tinlab Invited Speaker Series"
sitemap: false
permalink: /talk_series
---

# tinlab Invited Speaker Series (TISS)

Each semester, tinlab hosts talks by early career researchers covering diverse topics related to language, AI, cognition, and computation. If you are an early career researcher interested in giving a talk at our group or have speaker recommendations, please reach out to Najoung!

<style>
.talk-row {
  cursor: pointer;
  border-bottom: 1px solid #e0e0e0;
  padding: 15px 10px;
  transition: background-color 0.2s ease;
}
.talk-row:hover {
  background-color: #f9f9f9;
}
.talk-header {
  display: flex;
  font-size: 1.1em;
  align-items: baseline;
}
.talk-date {
  font-weight: bold;
  width: 150px;
  flex-shrink: 0;
}
.talk-speaker {
  width: 250px;
  padding-right: 20px;
  flex-shrink: 0;
}
.talk-title {
  flex-grow: 1;
  font-style: italic;
}
.talk-abstract {
  margin-top: 15px;
  padding: 15px;
  background-color: #fcfcfc;
  border-left: 4px solid #0055a4;
  border-radius: 4px;
  font-size: 1.05em;
  color: #333;
}
.nav-tabs {
  margin-bottom: 25px;
}
.nav-tabs > li > a {
  font-size: 1.1em;
  font-weight: bold;
}
</style>

<div markdown="0">

<!-- Nav tabs -->
<ul class="nav nav-tabs" role="tablist">
  {% for season in site.data.talks %}
  <li role="presentation" class="{% if forloop.first %}active{% endif %}">
    <a href="#{{ season.semester | slugify }}" aria-controls="{{ season.semester | slugify }}" role="tab" data-toggle="tab">{{ season.semester }}</a>
  </li>
  {% endfor %}
</ul>

<!-- Tab panes -->
<div class="tab-content">
  {% for season in site.data.talks %}
  <div role="tabpanel" class="tab-pane fade {% if forloop.first %}in active{% endif %}" id="{{ season.semester | slugify }}">
    
    {% assign sorted_talks = season.talks | sort: 'date' %}
    {% for talk in sorted_talks %}
    {% assign collapse_id = season.semester | slugify | append: "-" | append: forloop.index %}
    
    <div class="talk-row" {% if talk.abstract %}data-toggle="collapse" data-target="#{{ collapse_id }}" aria-expanded="false" aria-controls="{{ collapse_id }}"{% endif %}>
      <div class="talk-header">
        <div class="talk-date">{{ talk.date | date: "%B %-d" }}</div>
        <div class="talk-speaker">
          {% if talk.website and talk.website != "" %}
            <a href="{{ talk.website }}" target="_blank">{{ talk.speaker }}</a>
          {% else %}
            {{ talk.speaker }}
          {% endif %}
        </div>
        <div class="talk-title">
          {{ talk.title }}
          {% if talk.abstract %}
          <span class="pull-right glyphicon glyphicon-chevron-down" style="font-size: 0.8em; color: #888; padding-top: 5px;"></span>
          {% endif %}
        </div>
      </div>
      
      {% if talk.abstract %}
      <div class="collapse" id="{{ collapse_id }}">
        <div class="talk-abstract">
          <strong>Abstract:</strong> {{ talk.abstract | markdownify }}
        </div>
      </div>
      {% endif %}
    </div>
    
    {% endfor %}

  </div>
  {% endfor %}
</div>

</div>