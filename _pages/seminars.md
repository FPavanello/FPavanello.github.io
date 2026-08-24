---
layout: archive
title: "Talks & Presentations"
lede: "Conferences, workshops, seminars and invited lectures."
permalink: /seminars/
author_profile: true
redirect_from:
  - /talks/
---

{% include base_path %}

<p class="lg-leadin">Talks still to come are marked <span class="tag">scheduled</span>.</p>

{% comment %}
  A plain list rather than the year-gutter row used elsewhere: the year is
  already the section heading, so a gutter would sit empty on all but the
  handful of scheduled talks.
{% endcomment %}

{% for year in site.data.talks %}
<section class="lg-sec">
  <h2>{{ year.year }} <span class="count">{{ year.items.size }}</span></h2>
  <ul class="lg-talks">
    {% for t in year.items %}
      <li>
        {{ t.title }}{% if t.venue %} <span class="where">— {{ t.venue }}</span>{% endif %}
        {% if t.invited %}<span class="tag tag--warm">invited</span>{% endif %}
        {% if t.scheduled %}<span class="tag">scheduled</span>{% endif %}
      </li>
    {% endfor %}
  </ul>
</section>
{% endfor %}
