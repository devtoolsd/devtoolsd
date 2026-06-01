---
name: Starlette
slug: starlette
language: python
description: Lightweight ASGI framework and toolkit — the foundation that FastAPI and other async Python frameworks are built on.
website: https://starlette.io
github: encode/starlette
year: 2018
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: web
tags: [backend, async, asgi, python, websockets, api, lightweight]
related_frameworks: [fastapi, flask, django]
features:
  - "ASGI-native — runs on Uvicorn, Hypercorn, or Daphne"
  - "WebSocket support built in"
  - "Background tasks without a separate queue"
  - "Streaming responses and server-sent events"
  - "Static file serving and templating (Jinja2)"
  - "Session and cookie middleware"
  - "Test client for synchronous and async tests"
  - "Mount sub-applications — FastAPI is a Starlette subclass"
install:
  pip: "pip install starlette uvicorn"
---

Starlette provides the async primitives — request/response handling, routing, middleware, WebSockets, background tasks — that FastAPI and other frameworks build on. Used directly, it is a production-ready micro-framework for high-performance async Python services with no overhead beyond what you need.

## Quick start

```bash
pip install starlette uvicorn
```

```python
# app.py
from starlette.applications import Starlette
from starlette.requests import Request
from starlette.responses import JSONResponse
from starlette.routing import Route
from starlette.middleware.cors import CORSMiddleware

posts = []

async def list_posts(request: Request) -> JSONResponse:
    return JSONResponse(posts)

async def create_post(request: Request) -> JSONResponse:
    data = await request.json()
    post = {"id": len(posts) + 1, **data}
    posts.append(post)
    return JSONResponse(post, status_code=201)

async def get_post(request: Request) -> JSONResponse:
    post_id = int(request.path_params["id"])
    post = next((p for p in posts if p["id"] == post_id), None)
    if not post:
        return JSONResponse({"error": "Not found"}, status_code=404)
    return JSONResponse(post)

app = Starlette(routes=[
    Route("/posts", list_posts, methods=["GET"]),
    Route("/posts", create_post, methods=["POST"]),
    Route("/posts/{id:int}", get_post, methods=["GET"]),
])

app.add_middleware(CORSMiddleware, allow_origins=["*"])
```

```bash
uvicorn app:app --reload
```

## When to use

Use Starlette directly when you want a lightweight async Python framework without FastAPI's Pydantic dependency and automatic docs. It's ideal for services where you need WebSockets, streaming, or background tasks but don't need API documentation. FastAPI is a superset of Starlette — if you use FastAPI, you're using Starlette's routing, middleware, and test client. For most new projects, FastAPI provides better developer ergonomics; Starlette suits projects that want more control over their stack.
