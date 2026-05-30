# Architecture

devtools.directory is a fully static site. There is no server, no database, and no runtime.

---

## Build pipeline

```
content/*.md  +  data/abstracts/*.yaml
        │
        ▼
      Hugo (build)
        │
        ▼
    public/          ← static HTML + CSS + JS + index.json
        │
        ▼
  GitHub Pages       ← served on every push to main
```

Hugo reads all Markdown files, resolves cross-references by slug, runs templates, and writes static HTML. The entire site rebuilds in ~60ms.

---

## Filtering and search

No server-side queries. All filtering happens in the browser via two mechanisms:

**1. `data-*` attributes** — every content card has its metadata embedded as HTML attributes at build time:

```html
<div class="tool-item"
     data-language="python"
     data-frameworks="django fastapi"
     data-type="library"
     data-pricing="free">
```

JavaScript reads these attributes and toggles `filter-hidden` on each element. Instant, zero network requests.

**2. JSON index** — Hugo generates `/index.json` at build time containing all tools with their full metadata. Any page can `fetch('/index.json')` for cross-section queries.

For larger datasets (10k+ items), the upgrade path is [Pagefind](https://pagefind.app) — run `pagefind --site public` after the Hugo build, add one `<script>` tag, and you get full-text binary search.

---

## Schema system

`data/abstracts/*.yaml` defines the shape of every content type. Templates read these files to:

- Know which fields to render and how
- Validate required fields and emit warnings
- Resolve inheritance (`framework` merges `tool`'s fields before its own)

The schema is read at Hugo template render time — no separate build step or code generation.

---

## Cross-references

All relationships are plain slug strings in frontmatter, resolved at render time:

```go-html-template
{{/* Find the language page for a tool */}}
{{ $langPage := .Site.GetPage (printf "/languages/%s/" .Params.language) }}

{{/* Find all tools that reference a framework */}}
{{ range where .Site.RegularPages "Section" "tools" }}
  {{ if in .Params.frameworks $frameworkSlug }}...{{ end }}
{{ end }}
```

If a referenced slug has no content file, the reference is silently skipped — no 404, no build error.

---

## File structure

```
devtools.directory/
├── content/           ← all Data and List content files
├── data/
│   ├── abstracts/     ← schema definitions
│   └── categories.yaml
├── layouts/           ← Hugo HTML templates
│   ├── partials/      ← shared components (header, footer, tool-card, validate-abstract)
│   ├── tools/
│   ├── languages/
│   ├── frameworks/
│   ├── stacks/
│   └── ...
├── static/
│   └── css/main.css   ← One Dark Pro theme
├── hugo.toml          ← Hugo config
└── .github/
    └── workflows/
        └── deploy.yml ← build + deploy on push to main
```
