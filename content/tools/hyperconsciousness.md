---
name: Hyperconsciousness
slug: hyperconsciousness
website: https://github.com/louis030195/hyperconsciousness
description: Developer-alpha encrypted, append-only knowledge store with a Rust CLI and scoped, expiring MCP access for agents.
tool_type: cli
pricing: free
open_source: true
license: MIT
github: louis030195/hyperconsciousness
docs_url: https://github.com/louis030195/hyperconsciousness/blob/main/README.md
categories:
  - databases
tags:
  - knowledge-management
  - agent-memory
  - mcp
  - encryption
platforms:
  - linux
  - macos
languages:
  - rust
language: rust
features:
  - Encrypted, signed append-only records
  - Scoped, expiring grants for MCP access
  - Device synchronization
featured: false
---

Hyperconsciousness stores knowledge for humans and agents and exposes it through a CLI, MCP server and HTTP server. It is developer-alpha software, so APIs and commands may change.

Build from source using the prerequisites and commands in the [official README](https://github.com/louis030195/hyperconsciousness/blob/main/README.md#install-from-source), including Rust 1.88 and `cargo build --release --locked`.

Read the [security limits](https://github.com/louis030195/hyperconsciousness/blob/main/docs/CONSTRAINTS.md) before using it with private data. Grants control server access; they do not isolate a process that already has access to the files or keys. Hosted model providers can see returned plaintext. No independent security audit is claimed.
