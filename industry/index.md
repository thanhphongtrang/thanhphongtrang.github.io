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

{% include instrument.html show_stack=true %}

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

## A venture of my own

I am co-founder and chief product officer of **MySwedenLife**, an AI-guided
onboarding assistant for people moving to Sweden. More than 116,000 newcomers
arrive each year and meet the same maze of agencies I once did; the product turns
that into a personalized, step-by-step path through the essentials, from
*personnummer* to ID card, BankID and healthcare registration. It is live for
international students across eleven cities, with a journey for skilled workers in
build. The instinct is the one that runs through all my work: put AI inside a hard
human decision, and leave the person in charge of it.

---

The full set of product case studies from my industry years, including journey
mapping, growth modelling and a 27-market accessibility programme, lives in the
[portfolio archive](/portfolio/).
