---
layout: page
title: "News"
permalink: /news/
standfirst: "The full record. The three most recent items also sit on the home page."
description: "News and updates from Phong Trang: doctorate, publications, applied AI work."
---

<ul class="news">
{%- assign items = site.data.news | sort: "sort" | reverse -%}
{%- for item in items %}
  <li>
    <span class="when">{{ item.date }}</span>
    <p class="what">{{ item.text | markdownify | remove: "<p>" | remove: "</p>" | strip }}</p>
  </li>
{%- endfor %}
</ul>
