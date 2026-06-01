---
name: Gin
slug: gin
language: go
description: Fast, lightweight HTTP web framework for Go — radix tree router, middleware support, and idiomatic Go API.
logo: https://upload.wikimedia.org/wikipedia/commons/b/b1/Gin_Logo.svg
website: https://gin-gonic.com
github: gin-gonic/gin
year: 2014
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, go, api, rest, router, middleware, performance]
related_frameworks: [echo, fiber, chi]
features:
  - "Radix tree router — ~40× faster than standard `net/http` ServeMux"
  - "Middleware groups — apply auth, logging, rate limiting to route groups"
  - "Automatic JSON, XML, and form binding with struct tags"
  - "Built-in validation via `binding` struct tags (uses go-playground/validator)"
  - "Rendering helpers — JSON, XML, HTML, YAML, protobuf"
  - "Crash recovery middleware — panics become 500 responses"
  - "Named URL parameters and wildcard routes"
  - "Test mode and testable `gin.Engine` instances"
install:
  go: "go get -u github.com/gin-gonic/gin"
---

Gin's httprouter-based radix tree delivers roughly 40× the performance of a standard `net/http` router. Its chainable middleware, parameter binding, and JSON validation make it the most widely used Go web framework for REST APIs. Clean request/response helpers and extensive documentation make it the entry point for most Go web developers moving from `net/http`.

## Quick start

```bash
mkdir my-api && cd my-api
go mod init my-api
go get -u github.com/gin-gonic/gin
```

```go
// main.go
package main

import (
	"net/http"

	"github.com/gin-gonic/gin"
)

type Post struct {
	ID    int    `json:"id"`
	Title string `json:"title" binding:"required"`
	Body  string `json:"body"  binding:"required"`
}

var posts []Post

func main() {
	r := gin.Default()

	r.GET("/posts", func(c *gin.Context) {
		c.JSON(http.StatusOK, posts)
	})

	r.GET("/posts/:id", func(c *gin.Context) {
		id := c.Param("id")
		for _, p := range posts {
			if fmt.Sprint(p.ID) == id {
				c.JSON(http.StatusOK, p)
				return
			}
		}
		c.JSON(http.StatusNotFound, gin.H{"error": "post not found"})
	})

	r.POST("/posts", func(c *gin.Context) {
		var post Post
		if err := c.ShouldBindJSON(&post); err != nil {
			c.JSON(http.StatusBadRequest, gin.H{"error": err.Error()})
			return
		}
		post.ID = len(posts) + 1
		posts = append(posts, post)
		c.JSON(http.StatusCreated, post)
	})

	r.Run(":8080")
}
```

## When to use

Gin is the default choice for Go REST APIs. It's battle-tested, extensively documented, and has the largest Go web framework community. Choose Gin when you want familiar middleware-based request handling in Go. Echo is a close alternative with a slightly different API. Fiber is faster (built on fasthttp) but not compatible with `net/http` middleware. For minimal, stdlib-compatible routing, Chi is worth considering.
