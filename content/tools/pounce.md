---
name: Pounce
slug: pounce
website: https://lbliii.github.io/pounce/
description: Pure-Python ASGI server for Python 3.14 with thread workers on free-threaded builds and a low-overhead HTTP/1.1 path.
tool_type: platform
pricing: free
open_source: true
license: MIT
github: lbliii/pounce
docs_url: https://lbliii.github.io/pounce/
categories: [backend, cli-tools, devops]
tags: [asgi, server, http, streaming, free-threading, python, http2, http3, websockets]
languages: [python]
language: python
frameworks: [django, fastapi, starlette]
features:
  - "Runs standard ASGI applications with CLI and programmatic entry points"
  - "Uses shared-interpreter thread workers on free-threaded Python 3.14t and process workers on GIL builds"
  - "Built-in HTTP/1.1 fast path with request-smuggling and header-limit checks"
  - "Streaming responses with graceful shutdown and connection draining"
  - "Install-gated HTTP/2, HTTP/3, WebSocket, TLS, metrics, and tracing support"
  - "Frozen shared configuration with TOML and command-line configuration surfaces"
featured: false
---

Pounce is an ASGI server designed around the worker and concurrency model of Python 3.14. On free-threaded builds, worker threads share one interpreter and one application instance; on GIL builds, Pounce falls back to multiple processes. It serves standard ASGI frameworks, supports streamed responses, and keeps HTTP/2, HTTP/3, WebSocket, TLS, and observability integrations available as optional features.

```bash
pip install bengal-pounce
pounce serve --app myapp:app
```
