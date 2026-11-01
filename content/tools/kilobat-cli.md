---
name: Kilobat CLI
slug: kilobat-cli
website: https://github.com/seifip/kilobat-cli
description: macOS network diagnostics with JSON output, a terminal dashboard, and a local MCP server.
long_description: |
  Inspect DNS, latency, interfaces, and proxy routing from the terminal or expose
  diagnostics to an MCP client over local stdio. Requires macOS 14 or later;
  the Homebrew formula builds from source with Xcode 16 or later.
  The GPL-3.0-only CLI is separate from Kilobat's proprietary menu-bar app.
  Reading Wi-Fi names requires the companion app and Location permission.
tool_type: cli
pricing: free
open_source: true
license: GPL-3.0-only
github: seifip/kilobat-cli
docs_url: https://github.com/seifip/kilobat-cli#readme
categories:
  - cli-tools
  - terminal-tools
tags:
  - networking
  - diagnostics
  - dns
  - mcp
platforms:
  - macos
languages:
  - swift
language: swift
features:
  - JSON output for scripts
  - Interactive terminal dashboard
  - Local stdio MCP server
install: |
  brew install seifip/kilobat/kilobat
featured: false
---
