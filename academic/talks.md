---
layout: page
title: "Talks"
permalink: /academic/talks/
section: academic
standfirst: "Conference presentations and invited talks."
description: "Conference talks and invited presentations by Phong Trang."
---
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
