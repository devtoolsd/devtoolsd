---
title: How to Contribute
description: Contribute developer tools, books, courses, and resources to the open-source DevTools Directory via GitHub Pull Requests.
---

This directory is **100% open source** — all data is YAML files in the GitHub repository. No login needed. Contributions happen via Pull Requests.

> **Quick version:** Fork the repo → create a YAML file in the right `data/` directory → open a PR. Done.

## What you can add

- **Tools** — Dev tools, IDEs, frameworks, CLIs, databases, DevOps tools, etc.
- **Books** — Books about software development, architecture, career growth, etc.
- **Courses** — Online courses, tutorials, and learning programs
- **Resources** — Guides, cheatsheets, podcasts, newsletters, reference sites

---

## Adding a Tool

### 1. Create the file

Create `data/tools/your-tool-slug.yaml` in your fork.

### 2. Fill in the YAML

```yaml
name: Your Tool Name
slug: your-tool-slug        # must match filename, URL-safe
website: https://yourtool.dev
description: A short one-sentence description of what this tool does.
long_description: |         # optional, markdown supported
  More details about the tool, use cases, history, etc.

# Metadata
resource_type: editor                # editor | framework | library | cli | devops | database |
                            # testing | api | monitoring | platform | design | other
pricing: free               # free | freemium | paid
open_source: true
license: MIT                # optional

# Links
github: owner/repo          # optional, e.g. "microsoft/vscode"
docs_url: https://docs.yourtool.dev   # optional
logo: https://cdn.yourtool.dev/logo.png  # optional, must be https

# Categorisation
categories:
  - ides-editors
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
  - python

# Meta
featured: false             # set true only for widely-known tools
company: Your Company       # optional
```

### 3. Open a PR

- Title: `add: Tool Name`
- Keep the PR focused on one item

---

## Adding a Book

Create `data/books/your-book-slug.yaml`:

```yaml
name: The Pragmatic Programmer
slug: pragmatic-programmer
website: https://pragprog.com/titles/tpp20/
author: David Thomas, Andrew Hunt
year: 2019
description: A timeless guide to software craftsmanship.
free: false
tags:
  - software-engineering
  - career
  - best-practices
categories:
  - software-engineering
```

---

## Adding a Course

Create `data/courses/your-course-slug.yaml`:

```yaml
name: CS50's Introduction to Computer Science
slug: cs50
website: https://cs50.harvard.edu/x/
provider: Harvard / edX
author: David J. Malan
free: true
description: Harvard's introduction to computer science and programming.
tags:
  - beginner
  - computer-science
  - python
  - c
```

---

## Adding a Resource

Create `data/resources/your-resource-slug.yaml`:

```yaml
name: The Twelve-Factor App
slug: twelve-factor-app
website: https://12factor.net
resource_type: guide           # guide | website | cheatsheet | newsletter | podcast | video | repo
description: A methodology for building software-as-a-service apps.
free: true
tags:
  - architecture
  - best-practices
  - devops
```

---

## Guidelines

- **One item per PR** — makes reviewing faster
- **Accurate descriptions** — copy from the official site if unsure
- **No spam** — personal projects are welcome but must be genuinely useful
- **Logo URLs** must be `https://` — Wikipedia Commons and official CDNs are preferred
- **Slugs** must be lowercase, hyphenated, URL-safe, and match the filename

## Fixing existing data

Found a wrong URL, outdated description, or missing field? Edit the YAML file directly on GitHub using the ✏ Edit button on any tool page, and open a PR.

---

If you have questions, open an [issue on GitHub](https://github.com/dariubs/devtools.directory/issues).

**Thank you for contributing! ★**
