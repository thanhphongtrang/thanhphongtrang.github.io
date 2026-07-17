---
layout: page
title: "Portfolio archive"
permalink: /portfolio/
standfirst: "Product case studies from my industry years. Kept as provenance, not as headline."
description: "Archive of product management case studies from Phong Trang's industry years at Volvo Cars."
---

These are written in the register of the work they describe: metrics,
stakeholders, delivery. I keep them because they are the evidence behind the
builder half of what I do, and because showing the work beats asserting it. The
three that bear directly on my research are pulled out on
[Tools & industry work](/tools/).

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
