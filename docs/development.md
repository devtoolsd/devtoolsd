# Development

## Requirements

- [Hugo extended](https://gohugo.io/installation/) v0.100+

```bash
brew install hugo        # macOS
choco install hugo-extended  # Windows
snap install hugo --channel=extended  # Linux
```

## Run locally

```bash
hugo server
# → http://localhost:1313/  (live reload on file save)
```

## Build

```bash
hugo               # output → public/
hugo --minify      # minified production build
```

## Verify

```bash
hugo build 2>&1    # should show 0 errors, 0 warnings
```

## Search (Pagefind)

Search is powered by [Pagefind](https://pagefind.app) and only works after a full build + index step. The `hugo server` live-reload server does **not** include search.

To test search locally:

```bash
hugo --minify && npx -y pagefind --site public
# then serve public/ with any static server, e.g.:
npx serve public
```

In CI (GitHub Actions) the index step runs automatically after the Hugo build.

## Check validation warnings

Open any content page in the dev server. If a required field is missing, a yellow warning banner appears at the top of the page. All builds also emit `<!-- ABSTRACT VALIDATION: ... -->` HTML comments — grep for them in `public/` to audit content quality.

```bash
grep -r "ABSTRACT VALIDATION" public/ | head -20
```

## Add a new content type (core team)

1. Create `data/abstracts/{slug}.yaml` — define `extends`, `kind`, and `fields`
2. Create `content/{slug}/_index.md`
3. Create `layouts/{slug}/list.html` and `layouts/{slug}/single.html`
4. Add the section to the nav in `layouts/partials/header.html`
5. Update `CONTRIBUTING.md` with the new schema

## Edit templates

Templates live in `layouts/`. Hugo reloads them automatically during `hugo server`. The partial `layouts/partials/validate-abstract.html` runs on every content page — include it with:

```go-html-template
{{ partial "validate-abstract.html" . }}
```
