---
name: Extenshi MCP Server
slug: extenshi-mcp
website: https://catalog.extenshi.io/mcp
description: MCP server that brings browser-extension catalog search, security analysis, and pre-publish scanning into Claude, Claude Code, and Cursor.
long_description: |
  The Extenshi MCP server exposes the extension catalog over the Model Context Protocol, so an AI assistant can search across the Chrome, Firefox, and Edge stores, read an extension's security findings, pull market and competitor data, and consult the product documentation and CLI reference without leaving the conversation. It ships in two forms. The hosted remote connector speaks Streamable HTTP and authorizes with OAuth 2.1 — you add it by URL, sign in, and nothing runs on your machine — and it exposes the read, research, and docs tools. The local npm package runs over stdio with an API key and exposes the full tool set, including scanning a local build and publishing to the stores.
tool_type: api
pricing: freemium
open_source: false
logo: https://catalog.extenshi.io/logo.svg
docs_url: https://docs.extenshi.io/developers/mcp
categories:
  - extensions
  - backend
tags:
  - mcp
  - model-context-protocol
  - browser-extensions
  - ai-tools
  - security
platforms:
  - windows
  - macos
  - linux
  - web
languages:
  - typescript
features:
  - Search the cross-store extension catalog from an AI client
  - Read security findings and risk data for any extension
  - Market and competitor research over the catalog
  - Docs and CLI command reference as tools
  - Local mode adds pre-publish scanning and store publishing
install: |
  # hosted remote connector: add https://mcp.extenshi.io/mcp as a custom connector by URL
  # or run locally over stdio (Node 20+):
  npx @extenshi/mcp@latest
language: typescript
company: Extenshi
featured: false
---
