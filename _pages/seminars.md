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

{% for year in site.data.talks %}
<section class="lg-sec">
  <h2>{{ year.year }} <span class="count">{{ year.items.size }}</span></h2>
  {% for t in year.items %}
    <div class="lg-row">
      <div class="yr">{% if t.scheduled %}<span class="tag">scheduled</span>{% endif %}</div>
      <div class="what">
        {{ t.title }}{% if t.venue %} <span class="where">— {{ t.venue }}</span>{% endif %}
        {% if t.invited %}<span class="tag tag--warm">invited</span>{% endif %}
      </div>
    </div>
  {% endfor %}
</section>
{% endfor %}
