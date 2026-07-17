# AGENTS.md

Governance and orientation for any AI agent (or human) working on this site.
Read this whole file before touching anything. This file is public, like the
rest of the repo; anything sensitive lives in `.claude/` (gitignored, local).

## What this is

The personal academic site of Phong Trang, live at
<https://thanhphongtrang.github.io>. Jekyll, built natively by GitHub Pages.

**Branch is `master`. There is no other branch. A push to `master` deploys to
the live site in ~40 seconds. There is no staging. Never push without the
owner's explicit say-so.**

## Architecture (decided, do not relitigate)

- Jekyll + native GitHub Pages build. No Actions workflow, no framework,
  **zero JavaScript** on the page. ~8KB/page, one 12KB stylesheet, no
  webfonts, no trackers.
- The Gemfile pins the `github-pages` gem on purpose: local builds equal what
  actually deploys. Do not upgrade to Jekyll 4; native Pages would silently
  ignore it and you would be verifying a site that never ships.
- Hand-written theme. The old academicpages/Minimal Mistakes template was
  deleted deliberately. Do not reintroduce jQuery, Leaflet, Disqus, font
  packs, or any of it.
- Content edited monthly lives in `_data/*.yml`. Prose lives in root `.md`
  files. The point: the owner can add a news item from a phone's GitHub web
  UI and it self-deploys.

## Repo map

| Path | What it is |
|---|---|
| `_data/news.yml` | News feed. Ordered by `sort:` date. Home shows the 3 newest; `/news/` shows all. Has a TENSE FLAG comment. |
| `_data/publications.yml` | Publications, split `peer_reviewed:` / `other:`. Author strings AS PUBLISHED. |
| `_data/work.yml` | Research instrument + Volvo-era applied work + the Eliq line. |
| `_data/links.yml` | Footer profile links. `url: ~` hides an item until filled in. |
| `_layouts/` | `default` (shell), `page`, `portfolio` (adds provenance note + breadcrumb). |
| `_includes/` | `head`, `nav`, `footer`, `instrument` (shared research-instrument block). |
| `index.md` | Home: identity line, glance strip (CSS-only trajectory), bio, 3 newest news items, contact. Nothing else belongs here. |
| `research.md` `publications.md` `news.md` `tools.md` `teaching.md` `cv.md` | The pages. |
| `portfolio.md` + `_portfolio/` | Six archived industry case studies. Provenance, not headline. |
| `assets/css/style.css` | The one stylesheet. |
| `_config.yml` | Note the `defaults:` ordering comment; it is load-bearing. |

## Identity (the whole point)

One deliberate trajectory, not two careers. Researcher first, builder as the
differentiator. Identity line, verbatim, never reworded:

> I research how teachers keep professional judgment when AI joins the work.
> And I build the tools to study it.

The bio's spine is a closed loop: language teacher in Ho Chi Minh City →
analytics → four years at Volvo Cars building AI inside human decisions →
back to education for the doctorate. A return, not a pivot.

## Hard content rules

1. **Publishing name: `Phong Trang`, cites as `Trang, P.`** The master's
   thesis is indexed "Trang, T. T. P."; both are him. Cite every work as
   published, never retroactively normalised.
2. **The 2023 GUPEA item is a master's thesis, not a paper.** It stays under
   "Other research outputs", labelled. Never promote it to peer-reviewed.
3. **Eliq**: exactly one woven line under "Recently" on the Tools page. No
   logo, no employment-timeline block, never a "project", dates loose.
   **Eliq's clients are never named anywhere**, nor their products, nor
   marketing copy about them. If asked to add any of that, push back.
4. **No unpublished research findings.** The instrument is "in development".
   The 2024 Volvo study: describe the method (traces + survey, n=127), never
   results. The instrument repo (`graite-instrument`) went public 2026-07-17,
   Phase 0, synthetic data only, per its own README ("no participants, no
   network calls"). Linking is fine now. The no-findings rule still holds:
   never publish participant data, transcripts, or results from it here.
5. Nothing about immigration or visa status. No Eliq internal specifics.
6. **No em-dashes in any new prose.** En-dashes in year ranges (2023–2024)
   are fine. The archived `_portfolio/` case studies are the owner's own
   words and keep their em-dashes; **leave that prose alone**.
7. Credentials filter: story-evidence earns a page; generic prestige goes in
   the CV only. SISGP scholarship is surfaced (it explains Sweden). Volvo
   Global Graduate Program is CV-only. PMP is **not** held; do not list it.

## Local build (Windows, this machine)

Ruby 3.3 + DevKit is installed at `C:\Ruby33-x64` (on machine PATH). The
Windows-only `tzinfo-data` fix lives in `.bundle/Gemfile.local` (untracked;
`.bundle/config` points bundler at it). Do not add it to the tracked Gemfile.

```sh
cd thanhphongtrang.github.io
bundle exec jekyll build                # must be clean
bundle exec jekyll serve --no-watch     # http://127.0.0.1:4000
```

The parent directory's `.claude/launch.json` starts this server for browser
preview (it uses 8.3 short paths because the parent path contains a space).
In Git Bash, prefix `cmd`/`docker` calls with `MSYS_NO_PATHCONV=1` or paths
get mangled.

## Verification checklist (before any push)

1. `bundle exec jekyll build` exits clean.
2. Serve and crawl: every page, every `_portfolio/` item, every referenced
   asset returns 200. Compare referenced paths against files on disk.
3. Grep the built `_site/` for banned content: any Eliq client name (list in
   `.claude/private-context.md` if present locally), "PMP", em-dashes in
   pages you touched (portfolio pages exempt).
4. Check the `markdown="1"` rendering: `## News` must be an `<h2>`, not
   literal text, on the home page.
5. Contrast: check the maths, do not eyeball.
6. Report failures honestly. Flag pre-existing bugs; do not silently fix or
   silently ignore them.

## Gotchas that will bite you

- **kramdown does not parse markdown inside block-level HTML** without
  `markdown="1"`. `index.md` and several `_portfolio/*.md` depend on it.
- **`_config.yml` `defaults:` order matters**: last match wins. Generic
  first, specific last, or portfolio pages get the wrong layout.
- **Git on Windows has `core.ignorecase=true`**: case-only renames silently
  do not commit. Two-step `git mv` through a temp name.
- Jekyll's `:name` collection permalink slugifies (lowercases), so file case
  does not affect URLs.
- The `porfolio-img` → `portfolio-img` typo was fixed repo-wide. Do not
  reintroduce it.
- `AGENTS.md`, `CLAUDE.md`, `README.md` are in `_config.yml`'s `exclude:`
  list so they never appear in `_site/`.

## Open TODOs (owner's list, do not act without instruction)

1. `data-analyst-agent` repo link removed (404); TODO comment left in
   `_portfolio/data-analyst-agent.html`. Restore only if repo goes public.
2. Six orphaned testimonial photos (~928KB) in
   `assets/portfolio-img/testimonials/`; undecided.
3. Instrument screenshot: placeholder slots in `research.md` and `tools.md`
   (both render from `_includes/instrument.html`). The repo is public now
   (see hard rule 4), so a real capture is easier to get than before.
4. TENSE FLAG in `_data/news.yml`: "Starting" → "Started" once August 2026
   arrives.
5. Headshot possibly replaced with one that reads "researcher".

## Resolved (kept for history, do not re-open without instruction)

- ORCID (`0009-0001-4517-5416`) registered and wired into `_data/links.yml`
  and the JSON-LD `sameAs` in `_includes/head.html`. 2026-07-17.
- CV PDF at `files/phong-trang-cv.pdf`, generated from the live `/cv/` page
  via headless Chrome print-to-PDF, `cv_pdf: true` in `cv.md`. Regenerate the
  same way after any CV content change; there is no build-time automation
  for it. 2026-07-17.
- Instrument repo `graite-instrument` went public. 2026-07-17.

## The PhD vault (separate thing)

`D:\Graite` on the owner's other machine is a private PhD knowledge vault
with its own governance. **It is unrelated to this website** and is not
present on every machine. Protocol, on demand only, never scheduled:

- Consult it only when the owner explicitly asks ("check the vault for X").
- If the vault is not on the current machine, say so and ask the owner to
  either run the query there or grant access; do not guess at its contents.
- Never run vault session rituals for site work, and never copy vault
  material into this public repo. Anything derived from the vault that lands
  here must pass the content rules above (no unpublished findings).
