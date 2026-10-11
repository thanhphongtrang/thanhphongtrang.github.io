# thanhphongtrang.github.io

Personal site. Jekyll, hand-written theme, no framework, no JS, no trackers.
GitHub Pages builds it natively on push to `master`. There is no build step you
have to remember.

## Updating it

Almost everything you'll touch is a YAML file in `_data/`:

| To change | Edit |
|---|---|
| News feed | `_data/news.yml` — add an item, always set `sort` |
| Publications | `_data/publications.yml` |
| Instrument / industry work | `_data/work.yml` |
| Profile links | `_data/links.yml` |
| Blog | add `_posts/YYYY-MM-DD-slug.md` (see `_posts/_TEMPLATE.md.example`) |
| Menus and sub-tabs | `_data/nav.yml` (one line per page, plus the page file) |

Prose lives in the page files: `index.md` and `cv.md` at the repo root, the rest in
`academic/` and `industry/`.
Old product case studies live in `_portfolio/`.

You can edit any of these straight from the GitHub web UI — including on your
phone — and the site rebuilds itself.

## Running it locally

Needs Ruby (Windows: `C:\Ruby33-x64`). The `github-pages` gem pins Jekyll 3.9, so
what you build locally is what GitHub deploys. See `AGENTS.md` for details.

```sh
bundle exec jekyll build                # must be clean
bundle exec jekyll serve --no-watch     # http://127.0.0.1:4000
```

## Structure

```
_data/          content you edit regularly
_layouts/       default, page, portfolio, post, redirect
_includes/      head, nav, subtabs, footer, instrument
_posts/         blog posts: new post -> add _posts/YYYY-MM-DD-slug.md
academic/       academic pages (research, publications, teaching, talks, artefacts)
industry/       industry pages (case studies, MySwedenLife)
_portfolio/     industry case studies (archive)
assets/css/     one hand-written stylesheet
images/         headshot, favicons
files/          CV PDF
```
