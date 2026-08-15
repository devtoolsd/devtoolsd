---
name: Mac Developer Bridge
slug: mac-developer-bridge
website: https://github.com/alexanderradahl/mac-developer-bridge
description: Local MCP bridge that gives ChatGPT shell, file, PTY, background-job, and Codex-history access on macOS.
long_description: |
  Mac Developer Bridge lets a ChatGPT conversation operate the Mac where development work actually lives. It exposes arbitrary shell execution, unrestricted filesystem operations, real interactive PTY sessions, detached jobs, and read-only stored Codex history over MCP. The bridge itself makes no model calls and documents its intentionally unrestricted host-permission model in SECURITY.md.

tool_type: cli
pricing: free
open_source: true
license: MIT

github: alexanderradahl/mac-developer-bridge
docs_url: https://github.com/alexanderradahl/mac-developer-bridge#readme

categories:
  - cli-tools
  - terminal-tools

tags:
  - mcp
  - chatgpt
  - codex
  - ai-agents
  - local-first

platforms:
  - macos

languages:
  - javascript

features:
  - Arbitrary local shell execution
  - Unrestricted filesystem operations
  - Real interactive PTY sessions
  - Detached background jobs with logs
  - Read-only persisted Codex thread history
  - Explicit unlock latch, audit log, and kill switch

install: |
  git clone https://github.com/alexanderradahl/mac-developer-bridge.git
  cd mac-developer-bridge
  ./install.sh

language: javascript
featured: false
---
