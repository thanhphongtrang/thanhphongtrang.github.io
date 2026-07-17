# thanhphongtrang.github.io

Personal site. Jekyll, hand-written theme, no framework, no JS, no trackers.
GitHub Pages builds it natively on push to `main` — there is no build step you
have to remember.

## Updating it

Almost everything you'll touch is a YAML file in `_data/`:

| To change | Edit |
|---|---|
| News feed | `_data/news.yml` — add an item, always set `sort` |
| Publications | `_data/publications.yml` |
| Instrument / industry work | `_data/work.yml` |
| Profile links | `_data/links.yml` |

Prose lives in the page files at the repo root (`index.md`, `research.md`, …).
Old product case studies live in `_portfolio/`.

You can edit any of these straight from the GitHub web UI — including on your
phone — and the site rebuilds itself.

## Running it locally

Needs Docker (no Ruby install required):

```sh
docker run --rm -v "$PWD:/srv/jekyll" -p 4000:4000 jekyll/jekyll:4 \
  sh -c "bundle install && jekyll serve -H 0.0.0.0"
```

Then open <http://localhost:4000>.

To just build: swap `jekyll serve -H 0.0.0.0` for `jekyll build`. Output in `_site/`.

## Structure

```
_data/          content you edit regularly
_layouts/       default, page, portfolio
_includes/      head, nav, footer
_portfolio/     industry case studies (archive)
assets/css/     one hand-written stylesheet
images/         headshot, favicons
files/          CV PDF
```
