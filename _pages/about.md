---
permalink: /
title: "Filippo Pavanello"
lede: "I am an applied environmental economist with a main focus on the economics of adaptation to climate change."
layout: archive
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% include base_path %}

<section class="lg-sec">
  <h2>Introduction</h2>
  <div class="lg-intro">
    <p>
      I am an <strong>Assistant Professor (non-tenured)</strong> at the
      <a href="https://www.ifo.de/en">ifo Institute</a> and
      <a href="https://www.lmu.de/en/">LMU Munich</a>, and a <strong>member</strong> of the
      <a href="https://www.cesifo.org/en">CESifo Research Network</a>.
    </p>
    <p>
      I completed my PhD in Economics at the
      <a href="https://www.unibo.it/it">University of Bologna</a> in July 2024. My dissertation
      was awarded the
      <a href="https://www.eaere.org/best-european-doctoral-dissertation-award/">Best Doctoral Dissertation Award</a>
      from the European Association of Environmental and Resource Economists.
    </p>
    <p>
      I am also a research affiliate at the <a href="https://www.cmcc.it/">CMCC</a>,
      <a href="https://www.eiee.org/">EIEE</a>, and
      <a href="https://www.unive.it/">Ca' Foscari University of Venice</a>.
    </p>
    <p>
      You can find my full CV
      <a href="{{ site.cv_pdf | prepend: base_path }}">here</a>.
    </p>
    <p>
      You can email me here:
      {% comment %}
        The displayed text keeps the [at] convention, but the href needs a
        real address or the link opens a message that cannot be sent. Taken
        from _config.yml so it is not written down twice.
      {% endcomment %}
      <a href="mailto:{{ site.author.email }}">pavanello[at]ifo.de</a>
    </p>
  </div>
</section>

<section class="lg-sec">
  <h2>Research</h2>
  <p class="lg-leadin">My current research relates to:</p>
  <ul class="lg-themes">
    <li>the <strong>social costs of warmer temperatures</strong>, especially for health</li>
    <li>the <strong>adaptation response</strong> of households</li>
    <li>the <strong>uneven distribution</strong> of exposure to extreme heat and of access to adaptation</li>
    <li>the <strong>(unintended) effects of public policies</strong> on how socio-economic outcomes respond to temperature</li>
  </ul>
</section>

{% if site.data.news and site.data.news.size > 0 %}
<section class="lg-sec">
  <h2>News</h2>
  {% for item in site.data.news %}
    <div class="lg-row">
      <div class="yr">{{ item.date }}</div>
      <div class="what">{{ item.text | markdownify | remove: "<p>" | remove: "</p>" }}</div>
    </div>
  {% endfor %}
</section>
{% endif %}

{% comment %} Upcoming talks are pulled from _data/talks.yml — anything flagged `scheduled`. {% endcomment %}
{% assign upcoming = "" | split: "" %}
{% for year in site.data.talks %}
  {% assign scheduled = year.items | where: "scheduled", true %}
  {% assign upcoming = upcoming | concat: scheduled %}
{% endfor %}

{% if upcoming.size > 0 %}
<section class="lg-sec">
  <h2>Upcoming talks</h2>
  {% for t in upcoming %}
    <div class="lg-row">
      <div class="yr">{{ t.when }}</div>
      <div class="what">{{ t.title }}{% if t.venue %}<span class="where-line">{{ t.venue }}</span>{% endif %}</div>
    </div>
  {% endfor %}
</section>
{% endif %}
