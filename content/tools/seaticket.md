---
name: SeaTicket
slug: seaticket
website: https://seaticket.ai/
description: Open-source, self-hostable support center that brings GitHub, Discord, Discourse and email into one view and drafts replies with AI.
long_description: |
  SeaTicket is a support center for software projects and their communities. It connects GitHub issues and pull requests, Discord forum channels, Discourse forums and email into one workspace, and reads your knowledge sources such as Notion and Confluence.

  An AI agent drafts a reply to each new question from past resolved issues and documentation, with sources attached. A person approves, edits or rejects every draft before it is posted back to the original thread. Questions without an answer become tickets with full context.

  It also includes a public support portal with AI chat, documentation browsing and ticket tracking, and can be self-hosted with Docker Compose using the language and embedding models you configure.

tool_type: platform
pricing: freemium
open_source: true
license: Apache-2.0

github: seacloud-lab/seaticket
logo: https://seaticket.ai/static/img/SeaTicket-logo-black.png
docs_url: https://user-docs.seaticket.ai/

categories:
  - devops

tags:
  - support
  - customer-support
  - helpdesk
  - ticketing-system
  - community
  - ai
  - self-hosted

platforms:
  - linux

languages:
  - javascript
  - python

features:
  - Unified inbox for GitHub issues and PRs, Discord, Discourse and email
  - AI-drafted replies with sources, approved by a person before posting
  - Tickets for questions that need an engineer
  - Public support portal with AI chat and docs
  - Self-hostable with Docker Compose

install: |
  # Self-hosting with Docker Compose: follow the setup guide
  # https://user-docs.seaticket.ai/

language: javascript
company: SeaCloud Labs
featured: false
---
