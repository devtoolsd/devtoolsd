# Contributing

All content is a Markdown file with YAML frontmatter. No account, no form — just a PR.

## Quick steps

1. Fork the repository
2. Create a file in the right `content/` directory (see [Content Types](content-types.md))
3. Fill in the YAML fields
4. Open a PR titled `add: Name` or `fix: Name`

One item per PR. The full field reference is in [CONTRIBUTING.md](../CONTRIBUTING.md) at the repo root.

## Rules

- **Slugs** must be lowercase, hyphenated, URL-safe, and match the filename (`visual-studio-code.md` → `slug: visual-studio-code`)
- **`open_source`** must be accurate
- **Descriptions** should be one sentence, factual, copied from the official site if unsure
- **No spam** — personal projects are welcome if genuinely useful

## Logos

Prefer uploading the logo directly to the repo over linking to an external URL.

**Local logo** (preferred):

1. Add the file to `static/img/logos/{section}/{slug}.svg` (SVG strongly preferred; PNG accepted)
2. Name it exactly after the content slug: `visual-studio-code.svg`, not `vscode.svg`
3. Set in frontmatter: `logo: /img/logos/tools/visual-studio-code.svg`

**External URL** (fallback when no file is available):

```yaml
logo: https://upload.wikimedia.org/wikipedia/commons/...
```

Wikipedia Commons and official CDNs are reliable. Avoid hotlinking from personal sites or CDNs without a stability guarantee.

Logo is always optional — entries without one are rendered without an image.

## Editing existing entries

Use the **✏ Edit on GitHub** button on any page, or navigate to the file directly. PR title: `fix: Tool Name`.

## What goes where

| I want to add... | Directory |
|---|---|
| A developer tool, editor, CLI, database | `content/tools/` |
| A programming language | `content/languages/` |
| A framework (React, Django, Laravel...) | `content/frameworks/` |
| A tech stack (MERN, Django Stack...) | `content/stacks/` |
| A learning path (ordered steps) | `content/paths/` |
| A book | `content/books/` |
| A course | `content/courses/` |
| A guide, cheatsheet, podcast, newsletter | `content/resources/` |
| A blog post | `content/blog/` |

## Abstracts and schemas

Each directory has a matching schema in `data/abstracts/`. The schema documents required and optional fields, their types, and which other content types they reference. Adding new Abstracts requires a core team PR — community PRs add Data and List content only.
