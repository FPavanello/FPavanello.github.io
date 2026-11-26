---
layout: archive
title: "Working Papers"
lede: "Papers under review or in revision, circulating drafts, and projects at an earlier stage."
permalink: /wp/
author_profile: false
---

{% include base_path %}
{% assign wp = site.data.working_papers %}

{% if wp.under_review and wp.under_review.size > 0 %}
<section class="lg-sec">
  <h2>Revisions &amp; under review <span class="count">{{ wp.under_review.size }}</span></h2>
  {% for p in wp.under_review %}
    {% include paper.html paper=p kind="wp" %}
  {% endfor %}
</section>
{% endif %}

{% if wp.working_papers and wp.working_papers.size > 0 %}
<section class="lg-sec">
  <h2>Working papers <span class="count">{{ wp.working_papers.size }}</span></h2>
  {% for p in wp.working_papers %}
    {% include paper.html paper=p kind="wp" %}
  {% endfor %}
</section>
{% endif %}

{% if wp.progress and wp.progress.size > 0 %}
<section class="lg-sec">
  <h2>Work in progress <span class="count">{{ wp.progress.size }}</span></h2>
  {% for w in wp.progress %}
    <div class="lg-course">
      <h3>{{ w.title }}</h3>
      {% if w.authors %}<p>{% include author-list.html authors=w.authors urls=w.coauthor_urls %}</p>{% endif %}
      <p class="term">
        <span class="tag">{{ w.status }}</span>
        {% if w.project %}<span class="tag">{{ w.project }}</span>{% endif %}
        {% if w.links %}{% for l in w.links %}<a href="{{ l.url }}">{{ l.label }}</a>{% endfor %}{% endif %}
      </p>
      {% if w.funding %}<p class="lg-meta">Funded by {{ w.funding }}</p>{% endif %}
    </div>
  {% endfor %}
</section>
{% endif %}
