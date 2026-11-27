---
name: TokenDefrag
slug: token-defrag
website: https://github.com/yuseferi/token-defrag
description: Estimate potential context-token savings in Claude Code and OpenCode sessions without changing model requests.
tool_type: cli
pricing: free
open_source: true
license: MIT
github: yuseferi/token-defrag
docs_url: https://github.com/yuseferi/token-defrag#quick-start
categories:
  - cli-tools
tags:
  - coding-agents
  - token-usage
  - cost-estimation
platforms:
  - macos
  - linux
languages:
  - go
language: go
features:
  - Estimate potential savings offline from local session history.
  - Observe live requests in shadow mode without rewriting them.
install: |
  git clone https://github.com/yuseferi/token-defrag
  cd token-defrag
  make build
---
