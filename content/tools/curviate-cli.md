---
name: Curviate CLI
slug: curviate-cli
website: https://curviate.com
description: Official command-line interface for the Curviate API, letting an AI agent operate LinkedIn from the terminal.
long_description: |
  `@curviate/cli` wraps the Curviate API for search, messaging, connections, posts, and account
  management on LinkedIn, including Sales Navigator and Recruiter. It is built for coding agents as
  much as for interactive use: JSON output on every command, structured exit codes so an agent can
  branch on failure instead of parsing text, and a retrieval mode (`--mode`/`--max-age`) to pick
  cached or live data per call. Account-safety rate-limit budgets are built into the API it talks to.
tool_type: cli
pricing: paid
open_source: true
license: MIT

github: Curviate/curviate-cli
docs_url: https://docs.curviate.com

categories:
  - cli
  - apis

tags:
  - linkedin
  - automation
  - ai-agents
  - sales

platforms:
  - windows
  - macos
  - linux

languages:
  - typescript

features:
  - JSON output and structured exit codes designed for AI agents
  - Search, message, connect, post, and manage LinkedIn accounts from the terminal
  - Sales Navigator and Recruiter support
  - Cached-or-live retrieval mode (--mode/--max-age) and account-safety rate-limit budgets

install: |
  npm install -g @curviate/cli

language: typescript
company: Curviate
featured: false
---
