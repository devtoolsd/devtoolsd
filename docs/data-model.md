# Data Model

Three layers: **Abstracts** define schemas, **Data** files implement them, **Lists** aggregate them.

---

## Abstracts

Schema files in `data/abstracts/*.yaml`. Controlled by the core team.

```yaml
# data/abstracts/framework.yaml
name: Framework
slug: framework
extends: tool          # inherits all fields from tool
kind: data             # data | list
fields:
  - name: language
    type: ref
    target: language
    required: true     # overrides tool's optional language
  - name: related_frameworks
    type: list-ref
    target: framework
    required: false
```

### Inheritance hierarchy

```
base (empty root)
├── tool
│   ├── language   (extends tool)
│   └── framework  (extends tool)
├── book
├── course
├── resource
├── tag
├── stack          (kind: list)
└── path           (kind: list)
```

A child field with the same `name` as a parent field overrides it — used to make `language` required in `framework` while optional in `tool`.

### Field types

| type | description | extra |
|---|---|---|
| `string` | plain text | `format: url \| slug \| color` |
| `boolean` | true / false | — |
| `number` | integer or float | — |
| `date` | ISO date | — |
| `enum` | one value from a list | `values: [a, b, c]` |
| `ref` | single slug → another Data item | `target: abstract-slug` |
| `list-ref` | array of slugs | `target:`, `free_form: true` |

`free_form: true` on `list-ref` means plain strings are also valid — the value doesn't need a matching content file.

---

## Data

Content files in `content/{abstract-slug}/*.md`. The directory implies the abstract — no extra field needed.

```yaml
# content/frameworks/django.md
---
name: Django
slug: django
language: python           # ref → content/languages/python.md
description: Batteries-included Python web framework.
website: https://djangoproject.com
github: django/django
pricing: free
open_source: true
tool_type: web
tags: [web, orm, python]
related_frameworks: [flask, fastapi]
---
Optional Markdown body.
```

---

## Lists

Abstracts with `kind: list`. Support two inclusion modes:

```yaml
# content/stacks/django-stack.md
---
name: Django Stack
language: python
items:            # manually curated slugs
  - django
  - postgresql
  - redis
filters:          # auto-include matching items
  abstract: tool
  language: python
  tags: [web]
---
```

Items from both `items` and `filters` are merged and deduplicated at render time.

---

## Tags

Free-form strings work everywhere (`tags: [web, api]`). A tag gains a detail page at `/tags/{slug}/` only when `content/tags/{slug}.md` exists:

```yaml
# content/tags/web.md
---
name: web
slug: web
description: Web development tools and frameworks.
color: "#61afef"
---
```

---

## Validation

Every content page runs `validate-abstract.html` at render time.

- **Dev (`hugo server`)** — missing required fields show a visible warning banner.
- **All builds** — emit `<!-- ABSTRACT VALIDATION: missing "language" in frameworks/react.md -->` HTML comments.

No build failure — warnings are advisory, not blocking.
