---
name: Pydantic
slug: pydantic
language: python
description: Data validation using Python type hints — parse and validate JSON payloads, configs, and env vars at runtime.
website: https://docs.pydantic.dev
github: pydantic/pydantic
year: 2017
pricing: free
open_source: true
license: MIT
library_type: validation
tags: [validation, schema, python, type-hints, serialization, fastapi]
frameworks: [fastapi, django, starlette]
related_libraries: [requests, httpx, zod]
---

Pydantic v2 is rewritten in Rust for 5-50x performance improvements over v1. It turns annotated Python classes into data models that parse, coerce, and validate inputs automatically. FastAPI uses Pydantic for request/response schemas, generating OpenAPI docs from the same class definitions.
