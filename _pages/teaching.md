---
layout: archive
title: "Teaching & Supervision"
lede: "Courses at LMU Munich and Ca' Foscari University of Venice, and supervised theses."
permalink: /teaching/
author_profile: true
---

{% include base_path %}
{% assign t = site.data.teaching %}

{% if t.current and t.current.size > 0 %}
<section class="lg-sec">
  <h2>Currently teaching</h2>
  {% for c in t.current %}
    <div class="lg-course">
      <h3>{{ c.title }}</h3>
      <p>{{ c.programme }} · {{ c.institution }}</p>
      <p class="term">{{ c.term }}{% if c.role %} · {{ c.role }}{% endif %}</p>
    </div>
  {% endfor %}
</section>
{% endif %}

{% if t.past and t.past.size > 0 %}
<section class="lg-sec">
  <h2>Previous courses</h2>
  {% for c in t.past %}
    <div class="lg-row">
      <div class="yr">{{ c.term }}</div>
      <div class="what">
        <strong>{{ c.title }}</strong>{% if c.role %} <span class="tag">{{ c.role }}</span>{% endif %}
        {% if c.where %} <span class="where">— {{ c.where }}</span>{% endif %}
      </div>
    </div>
  {% endfor %}
</section>
{% endif %}

{% if t.supervision and t.supervision.size > 0 %}
<section class="lg-sec">
  <h2>Thesis supervision <span class="count">{{ t.supervision.size }}</span></h2>
  {% for s in t.supervision %}
    <div class="lg-row">
      <div class="yr">{{ s.year }}</div>
      <div class="what">
        <strong>{{ s.student }}</strong>
        <span class="where">— {{ s.thesis }}</span>
        <span class="tag{% if s.role == 'main advisor' %} tag--warm{% endif %}">{{ s.role }}</span>
      </div>
    </div>
  {% endfor %}
</section>
{% endif %}
