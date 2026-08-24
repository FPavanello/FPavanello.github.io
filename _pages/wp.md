---
layout: archive
title: "Working Papers"
lede: "Papers under review or in revision, and projects at an earlier stage."
permalink: /wp/
author_profile: true
---

{% include base_path %}

<section class="lg-sec">
  <h2>Under review &amp; revision <span class="count">{{ site.data.working_papers.papers.size }}</span></h2>
  {% for p in site.data.working_papers.papers %}
    {% include paper.html paper=p kind="wp" %}
  {% endfor %}
</section>

{% if site.data.working_papers.progress and site.data.working_papers.progress.size > 0 %}
<section class="lg-sec">
  <h2>Work in progress <span class="count">{{ site.data.working_papers.progress.size }}</span></h2>
  {% for w in site.data.working_papers.progress %}
    <div class="lg-course">
      <h3>{{ w.title }}</h3>
      <p>{% include author-list.html authors=w.authors urls=w.coauthor_urls %}</p>
      <p class="term">
        <span class="tag">{{ w.status }}</span>
        {% if w.project %}<span class="tag">{{ w.project }}</span>{% endif %}
        {% if w.links %}{% for l in w.links %}<a href="{{ l.url }}">{{ l.label }}</a>{% endfor %}{% endif %}
      </p>
    </div>
  {% endfor %}
</section>
{% endif %}
