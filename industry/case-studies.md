---
layout: page
title: "Case studies"
permalink: /industry/case-studies/
section: industry
standfirst: "AI products I built at Volvo Cars and Eliq, meant to help a person decide rather than to decide for them."
description: "Product case studies from Phong Trang's work at Volvo Cars and Eliq."
redirect_from:
  - /portfolio/
---

A different domain, yet the same question I now ask about teachers, and the reason
I recognised that question when I met it in education.

## Featured


{% for w in site.data.work.applied %}
<div class="card">
  <span class="thread">{{ w.thread }}</span>
  <h3>{{ w.title }}</h3>
  <p class="card-meta">{{ w.org }} · {{ w.years }}</p>
  <p>{{ w.summary }}</p>
  <ul class="outcomes">
    {%- for o in w.outcomes %}
    <li>{{ o }}</li>
    {%- endfor %}
  </ul>
  <p class="stack">{{ w.stack }}</p>
  <p class="pub-links"><a href="{{ w.url }}">Read the case study</a></p>
</div>
{% endfor %}

## All case studies

<ul class="pubs">
{%- assign items = site.portfolio | sort: "title" -%}
{%- for p in items %}
  <li>
    <p class="pub-title"><a href="{{ p.url }}">{{ p.title }}</a></p>
    {%- if p.excerpt %}
    <p class="pub-note">{{ p.excerpt | split: "<br/>" | first | strip_html | strip }}</p>
    {%- endif %}
  </li>
{%- endfor %}
</ul>
