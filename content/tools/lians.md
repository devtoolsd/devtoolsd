---
name: Lians
slug: lians
website: https://www.lians.ai/
description: Open-source memory for any AI agent, with a local-first MCP server, SDKs, and desktop setup.
long_description: |
  Lians gives AI agents durable memory across chats, sessions, tools, and models.
  It runs locally by default with SQLite, needs no Lians account or API key for
  the free Community edition, and works through MCP, plugins, or an SDK.

tool_type: other
pricing: freemium
open_source: true
license: Apache-2.0

github: Lians-ai/Lians
logo: https://raw.githubusercontent.com/Lians-ai/Lians/master/docs/assets/logo-blue.png
docs_url: https://github.com/Lians-ai/Lians/tree/master/docs

categories:
  - ai
  - cli-tools
  - developer-tools

tags:
  - agent-memory
  - ai-agents
  - local-first
  - mcp
  - model-context-protocol
  - sqlite

platforms:
  - windows
  - macos
  - linux

languages:
  - python

features:
  - Durable memory across chats, tools, models, and sessions
  - Local-first SQLite storage with no required account or API key
  - MCP server plus Python and TypeScript SDKs
  - Inspect, correct, and permanently delete saved memories

install: |
  uvx --from "lians-sdk[mcp]" lians-mcp

language: python
company: Lians
featured: false
---

Lians is a memory layer rather than another assistant: users keep their existing
agent and model while giving it a provider-neutral place to remember.
