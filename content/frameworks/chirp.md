---
name: Chirp
slug: chirp
language: python
description: HTML-first Python web framework for full pages, fragments, streaming HTML, and server-sent events with built-in hypermedia contract checks.
website: https://lbliii.github.io/chirp/
github: lbliii/chirp
year: 2026
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [web, backend, asgi, html-over-the-wire, htmx, hypermedia, streaming, sse, free-threading, python]
related_frameworks: [django, fastapi, flask, starlette]
features:
  - "Intent-oriented return types for pages, fragments, out-of-band swaps, streams, and server-sent events"
  - "htmx-aware negotiation between full-page and fragment responses"
  - "Streaming HTML, Suspense-style deferred blocks, and SSE support"
  - "Built-in routing, templates, forms, validation, sessions, authentication, and testing helpers"
  - "`chirp check` validates routes, template blocks, and hypermedia contracts before deployment"
  - "Designed for Python 3.14 and free-threaded Python 3.14t"
install:
  pip: "pip install bengal-chirp"
---

Chirp is a full-stack hypermedia framework for server-rendered Python applications. Route handlers express response intent with types such as `Page`, `Fragment`, `EventStream`, and `Suspense`; Chirp handles layout composition, htmx request behavior, streaming, and response rendering. Its application checker compiles routing, return declarations, template blocks, and registries into an inspectable contract that can be exercised from the CLI and tests.
