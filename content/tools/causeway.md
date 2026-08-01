---
name: Causeway
slug: causeway
website: https://wildernessinteractive.com/causeway
description: "Give your AI a real Chromium browser: Causeway exposes 52 MCP tools to navigate, read, click, type, screenshot, and run JavaScript through CDP."
long_description: |
  Causeway is a standalone Rust binary that gives an AI a real Chromium browser through two protocols: MCP over stdio from the AI to Causeway, and Chrome DevTools Protocol over WebSocket from Causeway to Chromium. The current source registers 52 tools for navigation, tabs, clicking, typing, forms, page and accessibility reading, JavaScript, cookies, network and console inspection, screenshots, downloads, PDFs, device emulation, dialogs, WebMCP discovery, and batched browser actions.

  Causeway uses the browser's real rendering and JavaScript environment rather than simulating a page. The normal bridge path needs no Node or Python runtime dependency. Build the binary with Cargo, configure the Chromium executable and CDP port in causeway.toml, and connect the process to Claude Code, Cursor, or another MCP client.

  The public repository is free to use, modify, and distribute under The Wilderness Interactive Open License, including commercial integration. The same license does not permit selling Causeway as a standalone product or selling access to it as a hosted service.
tool_type: cli
pricing: free
license: The Wilderness Interactive Open License
github: wilderness-interactive/causeway
docs_url: https://github.com/wilderness-interactive/causeway#readme
categories:
  - cli-tools
  - terminal-tools
tags:
  - mcp
  - mcp-server
  - browser-automation
  - ai-agents
  - chromium
  - chrome-devtools-protocol
  - cdp
  - rust
  - developer-tools
  - web-automation
  - workflow-automation
  - browser-control
languages:
  - rust
language: rust
features:
  - Real Chromium rendering and JavaScript through Chrome DevTools Protocol
  - Structured MCP tool calls over standard input and output
  - Navigation, tabs, clicks, typing, form filling, reading, and accessibility inspection
  - JavaScript, cookies, network and console inspection, screenshots, downloads, PDFs, and device emulation
  - One standalone Rust binary with no Node or Python dependency in the normal bridge path
  - Batched browser actions through the chain tool
install: |
  cargo build
company: Wilderness Interactive
featured: false
---
