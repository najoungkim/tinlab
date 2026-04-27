---
title: "tinlab - People"
layout: gridlay
excerpt: "tinlab - People"
sitemap: false
permalink: /people/
---

# People of tinlab

 **If you are interested in joining us, see the [Joining the lab]({{ site.url }}{{ site.baseurl }}/joining) page.**


Jump to [Research Team](#research-team), [Student collaborators](#student-collaborators), [Friends of tinlab](#friends-of-tinlab), and [Alumni](#alumni).

## Research Team
{% assign number_printed = 0 %}
{% for member in site.data.research_team %}

{% assign even_odd = number_printed | modulo: 3 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-4 clearfix" style="text-align: center; margin-bottom: 30px;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" style="display: block; width: 150px; height: 150px; object-fit: cover; margin: 0 auto 15px auto !important;" />
  <h4>{% if member.website %}{% if member.website contains '://' %}<a href="{{ member.website }}">{{ member.name }}</a>{% else %}<a href="{{ site.baseurl }}{{ member.website }}">{{ member.name }}</a>{% endif %}{% else %}{{ member.name }}{% endif %}</h4>
  <b>{{ member.info }}</b>
  {% if member.interests %}<br><i>{{ member.interests }}</i>{% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 2 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 3 %}
{% if even_odd != 0 %}
</div>
{% endif %}


## Student Collaborators
{% assign number_printed = 0 %}
{% for member in site.data.student_collaborators %}

{% assign even_odd = number_printed | modulo: 3 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-4 clearfix" style="text-align: center; margin-bottom: 30px;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" style="display: block; width: 150px; height: 150px; object-fit: cover; margin: 0 auto 15px auto !important;" />
  <h4>{% if member.website %}{% if member.website contains '://' %}<a href="{{ member.website }}">{{ member.name }}</a>{% else %}<a href="{{ site.baseurl }}{{ member.website }}">{{ member.name }}</a>{% endif %}{% else %}{{ member.name }}{% endif %}</h4>
  <b>{{ member.info }}</b>
  {% if member.interests %}<br><i>{{ member.interests }}</i>{% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 2 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 3 %}
{% if even_odd != 0 %}
</div>
{% endif %}


## Friends of tinlab
{% assign number_printed = 0 %}
{% for member in site.data.friends %}

{% assign even_odd = number_printed | modulo: 3 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-4 clearfix" style="text-align: center; margin-bottom: 30px;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" style="display: block; width: 150px; height: 150px; object-fit: cover; margin: 0 auto 15px auto !important;" />
  <h4>{% if member.website %}{% if member.website contains '://' %}<a href="{{ member.website }}">{{ member.name }}</a>{% else %}<a href="{{ site.baseurl }}{{ member.website }}">{{ member.name }}</a>{% endif %}{% else %}{{ member.name }}{% endif %}</h4>
  <b>{{ member.info }}</b>
  {% if member.interests %}<br><i>{{ member.interests }}</i>{% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 2 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 3 %}
{% if even_odd != 0 %}
</div>
{% endif %}


## Alumni
{% assign number_printed = 0 %}
{% for member in site.data.alumni_members %}

{% assign even_odd = number_printed | modulo: 3 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-4 clearfix" style="text-align: center; margin-bottom: 30px;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" style="display: block; width: 150px; height: 150px; object-fit: cover; margin: 0 auto 15px auto !important;" />
  <h4>{% if member.website %}{% if member.website contains '://' %}<a href="{{ member.website }}">{{ member.name }}</a>{% else %}<a href="{{ site.baseurl }}{{ member.website }}">{{ member.name }}</a>{% endif %}{% else %}{{ member.name }}{% endif %}</h4>
  <b>{{ member.info }}</b>{% if member.interests %}<br><i>{{ member.interests }}</i>{% endif %}{% if member.current %}<br>{{ member.current }}{% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 2 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 3 %}
{% if even_odd != 0 %}
</div>
{% endif %}



## Former affiliates
<div class="row">

<div class="col-sm-12 clearfix">
{% for member in site.data.former_affiliates %}
{{ member.name }}<br>
{% endfor %}
</div>

</div>

