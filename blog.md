---
layout: page
title: "Blog"
permalink: /blog/
standfirst: "Shorter pieces and working thoughts, from both sides of the bridge."
description: "Blog by Phong Trang: shorter pieces and working thoughts on AI, teaching and product work."
---

{%- if site.posts.size > 0 %}
<ul class="news">
{%- for post in site.posts %}
  <li>
    <span class="when">{{ post.date | date: "%-d %b %Y" }}</span>
    <p class="what"><a href="{{ post.url }}">{{ post.title }}</a>{% if post.standfirst %}. {{ post.standfirst }}{% endif %}</p>
  </li>
{%- endfor %}
</ul>
{%- else %}
<div class="empty">
  <p>First post coming soon.</p>
</div>
{%- endif %}

<p><a href="/feed.xml">RSS feed</a></p>
