---
layout: archive
title: "Teaching"
lede: "Courses at LMU Munich and Ca' Foscari University of Venice."
permalink: /teaching/
author_profile: false
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
        {% if c.where %}<span class="where-line">{{ c.where }}</span>{% endif %}
      </div>
    </div>
  {% endfor %}
</section>
{% endif %}

{% comment %}
  Thesis supervision is intentionally not shown. The records are still kept
  under `supervision:` in _data/teaching.yml; restoring the section is a
  matter of pasting this block back, no data to re-enter.

  <section class="lg-sec">
    <h2>Thesis supervision <span class="count">{{ t.supervision.size }}</span></h2>
    {% for s in t.supervision %}
      <div class="lg-row">
        <div class="yr">{{ s.year }}</div>
        <div class="what">
          <strong>{{ s.student }}</strong>
          <span class="where-line">{{ s.thesis }} <span class="tag{% if s.role == 'main advisor' %} tag--warm{% endif %}">{{ s.role }}</span></span>
        </div>
      </div>
    {% endfor %}
  </section>
{% endcomment %}
