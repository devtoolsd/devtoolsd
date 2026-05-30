---
title: About DevTools Directory
description: An open-source, community-maintained directory of developer tools, books, courses, and resources.
---

**DevTools Directory** is a curated, open-source listing of tools and learning resources for software developers.

## Why this exists

There are thousands of developer tools, and finding the right one for your stack is hard. This directory solves that by:

- **Curating** only genuinely useful tools and resources
- **Being transparent** — all data is YAML on GitHub, not locked in a database
- **Community-driven** — anyone can add or fix entries via a Pull Request
- **No lock-in** — MIT licensed, fork it, host your own

## How it works

All content lives in `data/` directories in the [GitHub repository](https://github.com/dariubs/devtools.directory):

```
data/
  tools/        ← one .yaml per tool
  books/        ← one .yaml per book
  courses/      ← one .yaml per course
  resources/    ← one .yaml per resource
  stacks/       ← technology stacks (MERN, Laravel, etc.)
```

A GitHub Action builds the static site with [Hugo](https://gohugo.io) and deploys it to [GitHub Pages](https://pages.github.com) on every commit to `main`.

## Contributing

See the [How to Contribute](/contribute/) page for step-by-step instructions. No account needed — just a GitHub account and a PR.

## License

MIT. Use, fork, or remix freely.
