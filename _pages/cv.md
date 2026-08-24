---
layout: archive
title: "Curriculum Vitae"
lede: "A short overview. The full CV is available as a PDF."
permalink: /cv/
author_profile: false
redirect_from:
  - /resume
---

{% include base_path %}
{% assign cv = site.data.cv %}

<p><a class="author__cv" href="{{ site.cv_pdf | prepend: base_path }}">Download full CV (PDF)</a></p>

<section class="lg-sec">
  <h2>Current position</h2>
  {% for r in cv.position %}
    <div class="lg-row">
      <div class="yr">{{ r.years }}</div>
      <div class="what"><strong>{{ r.what }}</strong>{% if r.where %}<span class="where-line">{{ r.where }}</span>{% endif %}</div>
    </div>
  {% endfor %}
</section>

<section class="lg-sec">
  <h2>Education</h2>
  {% for r in cv.education %}
    <div class="lg-row">
      <div class="yr">{{ r.years }}</div>
      <div class="what">
        <strong>{{ r.what }}</strong>{% if r.where %}<span class="where-line">{{ r.where }}</span>{% endif %}
        {% if r.note %}<p class="lg-note">{{ r.note }}</p>{% endif %}
      </div>
    </div>
  {% endfor %}
</section>

<section class="lg-sec">
  <h2>Previous positions</h2>
  {% for r in cv.past %}
    <div class="lg-row">
      <div class="yr">{{ r.years }}</div>
      <div class="what"><strong>{{ r.what }}</strong>{% if r.where %}<span class="where-line">{{ r.where }}</span>{% endif %}</div>
    </div>
  {% endfor %}
</section>

<section class="lg-sec">
  <h2>Grants</h2>
  {% for r in cv.funding %}
    <div class="lg-row">
      <div class="yr">{{ r.years }}</div>
      <div class="what">
        <strong>{{ r.what }}</strong>{% if r.amount %} — {{ r.amount }}{% endif %}
        {% if r.role %}<span class="tag{% if r.role contains 'PI' %} tag--warm{% endif %}">{{ r.role }}</span>{% endif %}
        {% if r.funder %}<span class="where-line">{{ r.funder }}</span>{% endif %}
      </div>
    </div>
  {% endfor %}
</section>
