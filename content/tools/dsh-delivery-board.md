---
name: dsh-delivery-board
slug: dsh-delivery-board
website: https://github.com/jerryxff26-alt/dsh-delivery-board
description: Codebase-native delivery board (standalone CLI + optional DSH plugin) with stages, handoff audit, soft WIP, weekly Markdown, and local kanban + Timeline.
long_description: |
  Keeps delivery stages, owners, handoffs, soft WIP limits, a weekly Markdown client report,
  and a local kanban with calendar Timeline in one in-repo file (`delivery.json` by default).
  Views are projections of the same state so humans and coding agents stay aligned in git.
  Runs standalone via `npx github:jerryxff26-alt/dsh-delivery-board` or as a DeepSeek Harness plugin.

tool_type: cli
pricing: free
open_source: true
license: MIT

github: jerryxff26-alt/dsh-delivery-board
docs_url: https://github.com/jerryxff26-alt/dsh-delivery-board#readme

categories:
  - cli-tools
  - devops
  - project-management

tags:
  - delivery
  - kanban
  - project-management
  - cli
  - productivity
  - git

platforms:
  - macos
  - linux
  - windows

languages:
  - typescript
  - javascript

features:
  - Stage pipeline stored in-repo
  - Handoff audit trail
  - Soft WIP limits
  - Weekly Markdown report
  - Local kanban + calendar Timeline
  - Standalone CLI or DeepSeek Harness plugin

install: |
  npx github:jerryxff26-alt/dsh-delivery-board
  # or as a DeepSeek Harness plugin:
  # dsh plugin --profile web add github:jerryxff26-alt/dsh-delivery-board

language: typescript
featured: false
---
