---
name: Chi
slug: chi
language: go
description: Lightweight, idiomatic Go router — composable middleware, 100% net/http compatibility, zero external dependencies.
website: https://go-chi.io
github: go-chi/chi
year: 2015
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, go, router, middleware, stdlib, idiomatic, minimal]
related_frameworks: [gin, echo, fiber]
features:
  - "100% compatible with `net/http` — any `http.Handler` or `http.HandlerFunc` works"
  - "Zero external dependencies — only uses Go standard library"
  - "Composable middleware groups via `r.Use()` and `r.Group()`"
  - "Context-based URL parameters via `chi.URLParam(r, \"id\")`"
  - "Route subrouters for modular application structure"
  - "Built-in middleware: Logger, Recoverer, RealIP, Timeout, Compress"
  - "Treemux-based router for fast URL matching"
  - "Named and wildcard routes with full RESTful routing support"
install:
  go: "go get github.com/go-chi/chi/v5"
---

Chi is built entirely on Go's standard `net/http` interface — any existing `http.Handler` works without modification. Its composable middleware groups, context-based routing, and zero external dependencies make it the choice of developers who want Go's stdlib performance with cleaner routing ergonomics. Chi is particularly popular for building APIs that need to stay close to the standard library while scaling to larger codebases.

## Quick start

```bash
go mod init my-api
go get github.com/go-chi/chi/v5
```

```go
// main.go
package main

import (
	"encoding/json"
	"net/http"

	"github.com/go-chi/chi/v5"
	"github.com/go-chi/chi/v5/middleware"
)

type Post struct {
	ID    int    `json:"id"`
	Title string `json:"title"`
	Body  string `json:"body"`
}

var posts []Post

func main() {
	r := chi.NewRouter()
	r.Use(middleware.Logger)
	r.Use(middleware.Recoverer)

	r.Get("/posts", func(w http.ResponseWriter, r *http.Request) {
		json.NewEncoder(w).Encode(posts)
	})

	r.Route("/posts/{id}", func(r chi.Router) {
		r.Get("/", func(w http.ResponseWriter, r *http.Request) {
			id := chi.URLParam(r, "id")
			w.Write([]byte("post: " + id))
		})
	})

	r.Post("/posts", func(w http.ResponseWriter, r *http.Request) {
		var p Post
		json.NewDecoder(r.Body).Decode(&p)
		p.ID = len(posts) + 1
		posts = append(posts, p)
		w.WriteHeader(http.StatusCreated)
		json.NewEncoder(w).Encode(p)
	})

	http.ListenAndServe(":3000", r)
}
```

## When to use

Chi is ideal when you want cleaner routing than bare `net/http` without pulling in a full framework. Its zero-dependency philosophy and stdlib compatibility mean you can swap it out or mix it with other `http.Handler`-compatible code effortlessly. Gin offers more batteries (binding, validation, rendering) at the cost of slightly more overhead. For maximum performance, Fiber (fasthttp-based) is faster but not `net/http` compatible.
