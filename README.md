# DevTools Directory

A curated, open-source knowledge base for developers — tools, languages, frameworks, stacks, books, courses, and learning paths. No database, no login, no backend. Just Markdown files and GitHub PRs.

**Site:** [devtools.directory](https://devtools.directory) · **Theme:** One Dark Pro · **Generator:** Hugo

---

## How it works

All content lives as `.md` files with YAML frontmatter in this repository. Hugo builds the site at every push to `main` and deploys it to GitHub Pages automatically.

```
content/
  tools/        → /tools/{slug}/
  languages/    → /languages/{slug}/
  frameworks/   → /frameworks/{slug}/
  stacks/       → /stacks/{slug}/
  paths/        → /paths/{slug}/
  books/        → /books/{slug}/
  courses/      → /courses/{slug}/
  resources/    → /resources/{slug}/
```

Every content type is defined by a schema in `data/abstracts/`. Fields are typed, required fields are documented, and inheritance is supported (`framework` extends `tool`, etc).

→ [docs/data-model.md](docs/data-model.md)

---

## Run locally

Requires [Hugo](https://gohugo.io/installation/) (extended).

```bash
brew install hugo   # macOS
hugo server         # → http://localhost:1313/
```

→ [docs/development.md](docs/development.md)

---

## Add content

1. Fork the repo
2. Create a file in the right `content/` directory
3. Fill in the YAML frontmatter
4. Open a PR titled `add: Name`

Full field schemas and examples: [CONTRIBUTING.md](CONTRIBUTING.md)

→ [docs/contributing.md](docs/contributing.md)

---

## Content types

| Type | Directory | Extends |
|---|---|---|
| Tool | `content/tools/` | base |
| Language | `content/languages/` | tool |
| Framework | `content/frameworks/` | tool |
| Stack | `content/stacks/` | base (list) |
| Path | `content/paths/` | base (list) |
| Book | `content/books/` | base |
| Course | `content/courses/` | base |
| Resource | `content/resources/` | base |
| Tag | `content/tags/` | base |

→ [docs/content-types.md](docs/content-types.md)

---

## Architecture

- **Static site** — Hugo generates HTML at build time, served from GitHub Pages
- **No server** — filtering and search run entirely in the browser via JS + `data-*` attributes
- **JSON index** — Hugo outputs `/index.json` at build time for cross-section queries
- **Schema system** — `data/abstracts/*.yaml` defines field types, required fields, and inheritance
- **Validation** — missing required fields emit warnings in dev mode

→ [docs/architecture.md](docs/architecture.md)

---

## Deploy

Push to `main`. GitHub Actions runs Hugo and deploys to GitHub Pages automatically.

→ [docs/deployment.md](docs/deployment.md)

---

## License

MIT
