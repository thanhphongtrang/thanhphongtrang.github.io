---
layout: default
title: "Home"
hide_title: true
---

<!-- markdown="1" is load-bearing: kramdown does not parse markdown inside a
     block-level HTML element without it, and the prose below silently renders
     as literal "## News" and "[GRAITE](/research/)". -->
<div class="wrap prose" markdown="1">

<div class="hero">
  <img src="{{ site.author.photo }}" alt="{{ site.author.photo_alt | strip_newlines | strip }}" width="272" height="272">
  <div>
    <h1 class="hero-name">{{ site.author.name }}</h1>
    <p class="identity">I research how teachers keep professional judgment when AI joins the work. <em>And I build the tools to study it.</em></p>
    <p class="stack">Python · LangGraph · Databricks · Codex · ATLAS.ti</p>
    <p class="affil">Doctoral researcher, University of Gothenburg (IPKL) · GRAITE · {{ site.author.location }}</p>
  </div>
</div>

<ol class="glance" aria-label="Trajectory at a glance">
  <li>
    <span class="flag flag-vn" aria-hidden="true"></span><span class="g-city">Ho Chi Minh City</span>
    <span class="g-org">University of Education</span>
    <span class="g-what">Language teacher, then analytics</span>
    <span class="g-when">2013–2020</span>
  </li>
  <li>
    <span class="flag flag-se" aria-hidden="true"></span><span class="g-city">Gothenburg</span>
    <span class="g-org">University of Gothenburg</span>
    <span class="g-what">M.Sc., SISGP-funded (0.5 MSEK)</span>
    <span class="g-when">2020–2022</span>
  </li>
  <li>
    <span class="flag flag-us" aria-hidden="true"></span><span class="g-city">New Jersey</span>
    <span class="g-org">Volvo Cars USA</span>
    <span class="g-what">Commercial learning &amp; learning analytics</span>
    <span class="g-when">2022–2023</span>
  </li>
  <li>
    <span class="flag flag-se" aria-hidden="true"></span><span class="g-city">Gothenburg</span>
    <span class="g-org"><a href="/tools/">Volvo Cars AB</a></span>
    <span class="g-what">GenAI product management</span>
    <span class="g-when">2023–2026</span>
  </li>
  <li>
    <span class="flag flag-se" aria-hidden="true"></span><span class="g-city">Gothenburg</span>
    <span class="g-org"><a href="/research/">University of Gothenburg</a></span>
    <span class="g-what">GRAITE doctorate: back to where it began</span>
    <span class="g-when">Aug 2026 →</span>
  </li>
</ol>

I started out teaching languages in Ho Chi Minh City, designing curricula and
watching closely what genuinely helped people learn. That curiosity pulled me into
analytics, first for an airline, then a consultancy, and eventually to Sweden,
where I spent four years at Volvo Cars building AI products that sit inside human
decisions: how a buyer searches for a car, how a care agent finds the right
answer, how an analyst reaches one. The longer I shipped that kind of software,
the louder one question grew. What happens to a professional's own judgment once a
capable machine joins the work? In 2024 I ran an internal study on exactly that,
and I could not put it down. From August 2026 I carry the question back to where I
began: a doctorate at the University of Gothenburg, in [GRAITE](/research/),
asking how teacher educators hold on to judgment and agency when they co-create
with generative AI.

## News

<ul class="news">
{%- assign items = site.data.news | sort: "sort" | reverse -%}
{%- for item in items limit: 3 %}
  <li>
    <span class="when">{{ item.date }}</span>
    <p class="what">{{ item.text | markdownify | remove: "<p>" | remove: "</p>" | strip }}</p>
  </li>
{%- endfor %}
</ul>

<p class="pub-links"><a href="/news/">All news →</a></p>

## Contact

I am glad to hear from teacher educators, researchers working on professional
judgment and human-AI interaction, and people building instruments for studying
real work. Email reaches me fastest:
[{{ site.author.email }}](mailto:{{ site.author.email }}). Scholar, GitHub and
LinkedIn sit in the footer.

</div>
