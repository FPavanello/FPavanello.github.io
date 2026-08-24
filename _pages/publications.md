---
layout: archive
title: "Publications"
lede: "Peer-reviewed articles, policy reports and book chapters."
permalink: /publications/
author_profile: true
---

{% include base_path %}

<section class="lg-sec">
  <h2>Peer-reviewed <span class="count">{{ site.data.publications.size }}</span></h2>
  {% for p in site.data.publications %}
    {% include paper.html paper=p kind="pub" %}
  {% endfor %}
</section>

{% if site.data.other_work.policy and site.data.other_work.policy.size > 0 %}
<section class="lg-sec">
  <h2>Policy work <span class="count">{{ site.data.other_work.policy.size }}</span></h2>
  {% for p in site.data.other_work.policy %}
    <article class="lg-paper lg-paper--nofig">
      <div>
        <h3>{% if p.url %}<a href="{{ p.url }}">{{ p.title }}</a>{% else %}{{ p.title }}{% endif %}</h3>
        <p class="lg-authors">{{ p.authors | replace: site.author_key, site.author_key_bold }}</p>
        <p class="lg-venue"><em>{{ p.venue }}</em> <span class="yr">· {{ p.year }}</span></p>
      </div>
    </article>
  {% endfor %}
</section>
{% endif %}

{% if site.data.other_work.chapters and site.data.other_work.chapters.size > 0 %}
<section class="lg-sec">
  <h2>Book chapters <span class="count">{{ site.data.other_work.chapters.size }}</span></h2>
  {% for p in site.data.other_work.chapters %}
    <article class="lg-paper lg-paper--nofig">
      <div>
        <h3>{% if p.url %}<a href="{{ p.url }}">{{ p.title }}</a>{% else %}{{ p.title }}{% endif %}</h3>
        <p class="lg-authors">{{ p.authors | replace: site.author_key, site.author_key_bold }}</p>
        <p class="lg-venue"><em>{{ p.venue }}</em> <span class="yr">· {{ p.year }}</span></p>
      </div>
    </article>
  {% endfor %}
</section>
{% endif %}
