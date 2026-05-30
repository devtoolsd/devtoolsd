# Content Types

Every content type corresponds to an abstract in `data/abstracts/`. The directory name implies the abstract — no extra declaration needed.

---

## Tool

**Directory:** `content/tools/` · **URL:** `/tools/{slug}/` · **Extends:** base

```yaml
---
name: Docker
slug: docker
description: Platform for building and running containerised applications.
website: https://docker.com
github: moby/moby
logo: https://...
tool_type: devops          # editor | framework | library | cli | devops | database |
                           # testing | api | monitoring | platform | design | other
pricing: freemium          # free | freemium | paid
open_source: true
license: Apache-2.0
language: go               # primary language slug
frameworks: [express]      # compatible framework slugs
platforms: [windows, macos, linux]
tags: [containers, devops]
company: Docker Inc.
featured: false
---
```

---

## Language

**Directory:** `content/languages/` · **URL:** `/languages/{slug}/` · **Extends:** tool

```yaml
---
name: Python
slug: python
description: Readable, batteries-included language for web, data, and automation.
website: https://python.org
github: python/cpython
logo: https://...
year: 1991
paradigm: [oop, functional, scripting]
typing: dynamic            # static | dynamic | gradual
compilation: interpreted   # compiled | interpreted | transpiled | jit
featured: true
tags: [web, data-science, ai]
---
```

Language hub pages auto-aggregate all frameworks, tools, books, courses, stacks, and paths that reference this language slug.

---

## Framework

**Directory:** `content/frameworks/` · **URL:** `/frameworks/{slug}/` · **Extends:** tool

```yaml
---
name: Django
slug: django
language: python           # required — links to /languages/python/
description: Batteries-included Python web framework.
website: https://djangoproject.com
github: django/django
logo: https://...
year: 2005
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: web
tags: [web, orm, mvc, python]
related_frameworks: [flask, fastapi]
---
```

---

## Stack

**Directory:** `content/stacks/` · **URL:** `/stacks/{slug}/` · **Extends:** base (kind: list)

```yaml
---
name: Django Stack
slug: django-stack
description: Python web stack with Django, PostgreSQL, and Redis.
color: "#092E20"
language: python
items:                     # manually curated tool/framework slugs
  - django
  - postgresql
  - redis
filters:                   # auto-include matching items
  abstract: tool
  language: python
  tags: [web]
related_stacks: [laravel, rails]
---
```

---

## Path

**Directory:** `content/paths/` · **URL:** `/paths/{slug}/` · **Extends:** base (kind: list)

```yaml
---
name: Learn Python Web Dev
slug: learn-python-web
description: From Python basics to a production Django app.
language: python
level: beginner            # beginner | intermediate | advanced
duration: "~3 months"
tags: [python, django, web]
steps:
  - type: course           # course | book | tool | framework | resource
    slug: cs50
    note: Start here.
  - type: framework
    slug: django
    note: The framework you'll build with.
  - type: tool
    slug: postgresql
    note: Production database.
---
```

---

## Book

**Directory:** `content/books/` · **URL:** `/books/{slug}/` · **Extends:** base

```yaml
---
name: The Pragmatic Programmer
slug: pragmatic-programmer
description: Timeless advice on software craftsmanship.
website: https://pragprog.com/titles/tpp20/
author: David Thomas, Andrew Hunt
year: 2019
free: false
language: ""               # optional — primary subject language
tags: [software-engineering, best-practices]
---
```

---

## Course

**Directory:** `content/courses/` · **URL:** `/courses/{slug}/` · **Extends:** base

```yaml
---
name: CS50
slug: cs50
description: Harvard's introduction to computer science.
website: https://cs50.harvard.edu
provider: edX
author: David Malan
free: true
language: ""               # optional
tags: [beginner, computer-science]
---
```

---

## Resource

**Directory:** `content/resources/` · **URL:** `/resources/{slug}/` · **Extends:** base

```yaml
---
name: The Twelve-Factor App
slug: twelve-factor-app
description: Methodology for building scalable, maintainable SaaS apps.
website: https://12factor.net
tool_type: guide           # guide | website | cheatsheet | newsletter | podcast | video | repo
free: true
tags: [devops, architecture, best-practices]
---
```

---

## Tag

**Directory:** `content/tags/` · **URL:** `/tags/{slug}/` · **Extends:** base

Tags are optional — free-form strings work everywhere. Create a file only when you want a detail page.

```yaml
---
name: web
slug: web
description: Web development tools, frameworks, and resources.
color: "#61afef"           # optional accent color
logo: https://...          # optional
---
```

---

## Blog Post

**Directory:** `content/blog/` · **URL:** `/blog/{slug}/` · **Outside the abstract system**

```yaml
---
title: Post Title
date: 2025-01-15
author: Your Name
tags: [devops, tutorial]
---

Markdown content here.
```
