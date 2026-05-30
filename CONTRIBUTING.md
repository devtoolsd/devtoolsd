# Contributing to DevTools Directory

All data lives as Markdown files with YAML frontmatter. No database, no login, no backend — just a PR.

## Quick start

1. Fork the repository
2. Create a file in the appropriate `content/` directory
3. Fill in the YAML frontmatter (see schemas below)
4. Open a Pull Request — title it `add: Name` or `fix: Name`

---

## Content directories

| Content type | Directory             | URL pattern               |
|--------------|-----------------------|---------------------------|
| Tools        | `content/tools/`      | `/tools/{slug}/`          |
| Languages    | `content/languages/`  | `/languages/{slug}/`      |
| Frameworks   | `content/frameworks/` | `/frameworks/{slug}/`     |
| Stacks       | `data/stacks/`        | `/stacks/{slug}/`         |
| Learning Paths | `content/paths/`    | `/paths/{slug}/`          |
| Books        | `content/books/`      | `/books/{slug}/`          |
| Courses      | `content/courses/`    | `/courses/{slug}/`        |
| Resources    | `content/resources/`  | `/resources/{slug}/`      |
| Blog posts   | `content/blog/`       | `/blog/{slug}/`           |

---

## Tool schema

File: `content/tools/your-tool-slug.md`

```markdown
---
name: Tool Name
slug: your-tool-slug
website: https://example.com
description: One sentence describing what this tool does.
long_description: |
  Optional extended description. Markdown supported.

tool_type: editor        # editor | framework | library | cli | devops | database |
                    # testing | api | monitoring | platform | design | other
pricing: free       # free | freemium | paid
open_source: true
license: MIT

github: owner/repo  # e.g. microsoft/vscode
logo: /img/logos/tools/my-tool.svg       # local preferred; https:// URL also accepted
docs_url: https://docs.example.com

categories:
  - ides-editors    # use slugs from data/categories.yaml
  - extensions

tags:
  - productivity
  - autocomplete

platforms:
  - windows
  - macos
  - linux

languages:
  - typescript

features:
  - Intelligent code completion
  - Built-in Git integration

install: |
  # e.g.
  brew install --cask visual-studio-code

language: typescript   # primary language slug → links to /languages/typescript/
frameworks:            # frameworks this tool works with (slugs)
  - react
  - nextjs

company: Microsoft
featured: false
---
```

---

## Book schema

File: `content/books/your-book-slug.md`

```markdown
---
name: Book Title
slug: your-book-slug
website: https://example.com/buy
author: Author Name
year: 2023
description: One sentence description.
free: false
tags:
  - software-engineering
  - best-practices
categories:
  - software-engineering
---

Optional extended Markdown description below the frontmatter.
```

---

## Course schema

File: `content/courses/your-course-slug.md`

```markdown
---
name: Course Title
slug: your-course-slug
website: https://example.com/course
provider: Coursera
author: Instructor Name
free: true
description: What this course teaches.
tags:
  - python
  - beginner
---
```

---

## Resource schema

File: `content/resources/your-resource-slug.md`

```markdown
---
name: Resource Name
slug: your-resource-slug
website: https://example.com
tool_type: guide       # guide | website | cheatsheet | newsletter | podcast | video | repo
description: What this resource is about.
free: true
tags:
  - architecture
  - devops
---
```

---

## Stack schema

Stacks live in `data/stacks/` as plain YAML (no frontmatter needed).

File: `data/stacks/your-stack-slug.yaml`

```yaml
name: Stack Name
slug: your-stack-slug
description: One sentence overview.
long_description: |
  Extended Markdown description.
color: "#c678dd"    # accent color for this stack (One Dark Pro hex)
language: javascript  # dominant language slug
frameworks:           # framework slugs used in this stack
  - react
  - express
tools:
  - visual-studio-code   # slugs matching content/tools/*.md filenames
  - nodejs
  - postgresql
related_stacks:
  - mern             # slugs matching other data/stacks/*.yaml filenames
tags:
  - javascript
  - full-stack
```

---

## Language schema

File: `content/languages/your-language-slug.md`

```markdown
---
name: Python
slug: python
description: One sentence pitch.
logo: /img/logos/languages/python.svg    # or https:// URL
website: https://python.org
github: python/cpython
year: 1991
paradigm: [oop, functional, scripting]
typing: dynamic        # static | dynamic | gradual
compilation: interpreted  # compiled | interpreted | transpiled | jit
featured: false
tags: [web, data-science, scripting]
---

Optional extended Markdown body describing the language ecosystem.
```

---

## Framework schema

File: `content/frameworks/your-framework-slug.md`

```markdown
---
name: Django
slug: django
language: python       # parent language slug → links to /languages/python/
description: One sentence pitch.
logo: /img/logos/frameworks/django.svg   # or https:// URL
website: https://djangoproject.com
github: django/django
year: 2005
pricing: free          # free | freemium | paid
open_source: true
license: BSD-3-Clause
tool_type: web         # web | mobile | desktop | data | testing | other
tags: [web, orm, mvc, python]
related_frameworks: [flask, fastapi]   # sibling framework slugs
---

Optional extended Markdown body.
```

---

## Learning Path schema

File: `content/paths/your-path-slug.md`

```markdown
---
name: Learn Python Web Dev
slug: learn-python-web
description: One sentence summary.
language: python       # language slug
level: beginner        # beginner | intermediate | advanced
duration: "~3 months"
tags: [python, django, web]
steps:
  - type: course       # course | book | tool | framework | resource
    slug: cs50
    note: Why this step matters.
  - type: framework
    slug: django
    note: The framework you'll build with.
  - type: tool
    slug: postgresql
    note: Your production database.
---

Optional Markdown body with context, prerequisites, and tips.
```

---

## Blog post schema

File: `content/blog/your-post-slug.md`

```markdown
---
title: Post Title
date: 2025-01-15
author: Your Name
tags:
  - devops
  - tutorial
---

Your Markdown content here.
```

---

## Guidelines

- **One item per PR** — easier to review
- **Accurate descriptions** — copy from official site if unsure
- **Logos**: upload SVG/PNG to `static/img/logos/{section}/{slug}.svg` and set `logo: /img/logos/tools/slug.svg`; an external `https://` URL is accepted as fallback
- **Slugs** must be lowercase, hyphenated, URL-safe, and match the filename
- **No spam** — personal projects welcome if genuinely useful
- **Open source** flag must be accurate

## Editing existing entries

Use the ✏ "Edit on GitHub" button on any page, or navigate to the file directly and edit it. Open a PR with title `fix: Tool Name`.

---

Questions? Open an [issue](https://github.com/dariubs/devtools.directory/issues).
