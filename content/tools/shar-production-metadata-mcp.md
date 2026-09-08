---
name: SHAR Production Metadata MCP
slug: shar-production-metadata-mcp
website: https://sharprod.com/
description: Read-only CLI and MCP server that validates rights-aware production metadata manifests.
long_description: |
  SHAR Production provides AI-hybrid video-production services. This MIT-licensed local Node.js tool validates rights-aware production metadata manifests and returns a releasability result. It runs over stdio, makes no network calls, does not write files, and does not handle credentials.
tool_type: cli
pricing: free
open_source: true
license: MIT
github: SHARProduction/production-metadata-mcp
docs_url: https://github.com/SHARProduction/production-metadata-mcp#readme
categories:
  - developer-tools
  - testing
tags:
  - mcp
  - metadata-validation
  - rights-aware
platforms:
  - windows
  - macos
  - linux
languages:
  - javascript
language: javascript
features:
  - Validates rights-aware production metadata manifests
  - Returns a deterministic releasability result
  - Runs locally with no network or file-write access
install: |
  npx -y @sharproduction/production-metadata-mcp
company: SHAR Production
featured: false
---