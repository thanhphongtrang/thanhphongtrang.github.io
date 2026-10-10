---
layout: page
title: "Publications"
permalink: /academic/publications/
section: academic
redirect_from:
  - /publications/
standfirst: "Peer-reviewed work and other research output."
description: "Publications by Phong Trang, including ECIS 2026 and work on chatbots for learning in citizen science."
---

{%- assign scholar = site.data.links | where: "name", "Google Scholar" | first -%}
The complete and current list lives on [Google Scholar]({{ scholar.url }}).

## Peer-reviewed

<ul class="pubs">
{%- for p in site.data.publications.peer_reviewed %}
  <li>
    <p class="pub-title">{{ p.title }}</p>
    <p class="pub-authors">{{ p.authors | markdownify | remove: "<p>" | remove: "</p>" | strip }}</p>
    <p class="pub-venue">{{ p.venue }}, {{ p.year }}</p>
    {%- if p.note %}<p class="pub-note">{{ p.note }}</p>{% endif -%}
    {%- if p.links %}
    <p class="pub-links">
      {%- for l in p.links %}<a href="{{ l.url }}">{{ l.text }}</a>{% endfor -%}
    </p>
    {%- endif %}
  </li>
{%- endfor %}
</ul>

## Other research outputs

Not peer-reviewed, and marked as such, but part of the same line of questioning.

<ul class="pubs">
{%- for p in site.data.publications.other %}
  <li>
    <p class="pub-title">{{ p.title }}{% if p.kind %}<span class="status-tag">{{ p.kind }}</span>{% endif %}</p>
    <p class="pub-authors">{{ p.authors | markdownify | remove: "<p>" | remove: "</p>" | strip }}</p>
    <p class="pub-venue">{{ p.venue }}, {{ p.year }}</p>
    {%- if p.note %}<p class="pub-note">{{ p.note }}</p>{% endif -%}
    {%- if p.links %}
    <p class="pub-links">
      {%- for l in p.links %}<a href="{{ l.url }}">{{ l.text }}</a>{% endfor -%}
    </p>
    {%- endif %}
  </li>
{%- endfor %}
</ul>
