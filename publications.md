---
layout: page
title: "Publications & talks"
permalink: /publications/
standfirst: "Peer-reviewed work, plus the research outputs that are not papers."
description: "Publications and talks by Phong Trang, including ECIS 2026 and work on chatbots for learning in citizen science."
---

{%- assign scholar = site.data.links | where: "name", "Google Scholar" | first -%}
The complete and current list lives on [Google Scholar]({{ scholar.url }}).

<p class="pub-note" style="margin-bottom:2rem">
  A note on the name: my master's thesis is indexed as <em>Trang, T. T. P.</em> and
  my ECIS paper as <em>Trang, P.</em> Both are me; going forward I publish as
  <strong>{{ site.author.cite_as }}</strong>
</p>

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

<div class="empty">
  <p>Nothing here yet. The doctorate starts in August 2026; this section will fill.</p>
</div>
