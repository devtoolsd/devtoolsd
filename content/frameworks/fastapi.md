---
name: FastAPI
slug: fastapi
language: python
description: Modern, async Python web framework with automatic OpenAPI docs and Pydantic-powered type validation.
logo: https://fastapi.tiangolo.com/img/logo-margin/logo-teal.png
website: https://fastapi.tiangolo.com
github: tiangolo/fastapi
year: 2018
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, api, rest, async, openapi, pydantic, python]
related_frameworks: [flask, django, starlette]
features:
  - "Automatic OpenAPI and Swagger UI docs generated from your code"
  - "Type hint-based request/response validation via Pydantic"
  - "Async-first with native `async def` support via Starlette"
  - "Dependency injection system for auth, DB sessions, and shared logic"
  - "One of the fastest Python frameworks — comparable to Node.js and Go"
  - "Path parameters, query parameters, and request bodies with zero boilerplate"
  - "Built-in OAuth2, JWT, and HTTP Basic auth helpers"
  - "WebSocket support out of the box"
install:
  pip: "pip install fastapi uvicorn"
---

FastAPI is a modern Python web framework built for building APIs fast — both in development speed and runtime performance. It uses Python type hints to drive automatic validation, serialization, and OpenAPI documentation, eliminating an entire category of boilerplate. Under the hood it's built on Starlette (ASGI) and Pydantic, making it fully async-capable and production-ready with Uvicorn or Gunicorn. It has become the go-to Python API framework for ML serving, microservices, and greenfield REST APIs.

## Quick start

```bash
pip install fastapi uvicorn
```

```python
# main.py
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str
    price: float
    in_stock: bool = True

items: dict[int, Item] = {}

@app.get("/")
async def root():
    return {"message": "Hello from FastAPI"}

@app.get("/items/{item_id}")
async def get_item(item_id: int) -> Item:
    if item_id not in items:
        raise HTTPException(status_code=404, detail="Item not found")
    return items[item_id]

@app.post("/items", status_code=201)
async def create_item(item: Item) -> Item:
    item_id = len(items) + 1
    items[item_id] = item
    return item
```

```bash
# Run the server — docs at http://localhost:8000/docs
uvicorn main:app --reload
```

## When to use

FastAPI is the best choice for Python REST APIs and ML model serving endpoints. Its combination of auto-docs, Pydantic validation, and async performance makes it ideal for data science teams exposing models or microservice backends. For a full-featured web application with an admin panel, Django is the better choice. For very simple scripts-turned-servers, Flask has less setup overhead.
