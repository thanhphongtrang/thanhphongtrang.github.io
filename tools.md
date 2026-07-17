---
layout: page
title: "Tools & industry work"
permalink: /tools/
standfirst: "The instrument I am building for the doctorate, and the years of product work that taught me how to build it."
description: "The research instrument Phong Trang is building, plus AI product work at Volvo Cars putting AI inside human decisions."
---

I build the things I study with. That is not a hobby bolted onto the research; it
is the reason the research can ask what it asks.

## The research instrument

{% assign i = site.data.work.instrument %}

### {{ i.title }}<span class="status-tag">{{ i.status }}</span>

{{ i.summary }}

{{ i.detail }}

<div class="shot-placeholder">
  <p><strong>Screenshot placeholder</strong><br>
  An interface capture goes here once the instrument reaches a presentable state.</p>
</div>

<p class="stack">{{ i.stack }}</p>

{{ i.note }}

*{{ i.repo_note }}*

## AI inside human decisions

Four years at Volvo Cars, building AI meant to help a person decide rather than to
decide for them. A different domain, yet the same question I now ask about
teachers, and the reason I recognised that question when I met it in education.

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

## Recently

{{ site.data.work.recent.summary }}

## Also

I co-founded **MySwedenLife**, a side venture helping newcomers navigate settling
in Sweden. It stays a side venture, but it is the other place I keep my hands in
building things people rely on.

---

The full set of product case studies from my industry years, including journey
mapping, growth modelling and a 27-market accessibility programme, lives in the
[portfolio archive](/portfolio/).
