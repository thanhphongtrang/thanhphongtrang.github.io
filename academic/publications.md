---
layout: page
title: "Publications & talks"
permalink: /publications/
standfirst: "Peer-reviewed work and other research output"
description: "Publications and talks by Phong Trang, including ECIS 2026 and work on chatbots for learning in citizen science."
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

## Talks

{%- assign talks = site.data.talks | sort: "sort" | reverse -%}
{%- if talks and talks.size > 0 %}
<ul class="pubs">
{%- for t in talks %}
  <li>
    <p class="pub-title">{{ t.title }}</p>
    <p class="pub-authors">{{ t.role }}</p>
    <p class="pub-venue">{{ t.event }}, {{ t.venue }}, {{ t.date }}</p>
    {%- if t.note %}<p class="pub-note">{{ t.note }}</p>{% endif -%}
    {%- if t.links %}
    <p class="pub-links">
      {%- for l in t.links %}<a href="{{ l.url }}">{{ l.text }}</a>{% endfor -%}
    </p>
    {%- endif %}
  </li>
{%- endfor %}
</ul>
{%- else %}
<div class="empty">
  <p>Nothing here yet. The doctorate starts in August 2026; this section will fill.</p>
</div>
{%- endif %}
