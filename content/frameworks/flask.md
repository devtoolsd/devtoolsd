---
name: Flask
slug: flask
language: python
description: Lightweight Python web micro-framework — minimal core, WSGI-based, and highly extensible via blueprints and extensions.
logo: https://upload.wikimedia.org/wikipedia/commons/3/3c/Flask_logo.svg
website: https://flask.palletsprojects.com
github: pallets/flask
year: 2010
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: web
tags: [backend, web, api, rest, python, micro, wsgi]
related_frameworks: [django, fastapi, starlette]
features:
  - "Minimal core — routing, request/response, and Jinja2 templates"
  - "Blueprints for modular application structure"
  - "Large extension ecosystem — Flask-SQLAlchemy, Flask-Login, Flask-Migrate"
  - "Development server with debugger and auto-reloader"
  - "Context locals — `request`, `g`, `session` available without threading boilerplate"
  - "WSGI-based — deploy on Gunicorn, uWSGI, or any WSGI server"
  - "Easy to add just the parts you need — no ORM or auth forced on you"
install:
  pip: "pip install flask"
---

Flask gives you routing, templates, and a request context — nothing more. Everything else (ORM, auth, migrations) comes from the large ecosystem of Flask extensions. Its simplicity makes it the go-to for small APIs, microservices, internal tools, and projects where Django's batteries are overhead. Flask has no required project layout, so it's quick to prototype and easy to structure exactly as your project demands.

## Quick start

```bash
pip install flask
```

```python
# app.py
from flask import Flask, jsonify, request, abort

app = Flask(__name__)

posts = [
    {"id": 1, "title": "Hello Flask", "body": "Getting started."},
]

@app.get("/posts")
def list_posts():
    return jsonify(posts)

@app.get("/posts/<int:post_id>")
def get_post(post_id):
    post = next((p for p in posts if p["id"] == post_id), None)
    if post is None:
        abort(404)
    return jsonify(post)

@app.post("/posts")
def create_post():
    data = request.get_json()
    new_post = {"id": len(posts) + 1, **data}
    posts.append(new_post)
    return jsonify(new_post), 201

if __name__ == "__main__":
    app.run(debug=True)
```

```bash
flask run --debug
# Visit http://127.0.0.1:5000/posts
```

## When to use

Flask is the best choice for small-to-medium Python APIs, internal tools, and projects where you want to pick your own ORM and auth strategy. Its lack of opinions is a feature — not a limitation — when the project's needs are clearly defined. For larger applications with complex data models, Django's batteries save significant time. For high-throughput async APIs, FastAPI offers better performance and automatic docs.
