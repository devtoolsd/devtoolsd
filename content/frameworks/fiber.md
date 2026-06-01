---
name: Fiber
slug: fiber
language: go
description: Express-inspired Go framework built on top of Fasthttp — the fastest Go web framework with a Node.js-like API.
logo: https://raw.githubusercontent.com/gofiber/docs/master/static/img/logo.svg
website: https://gofiber.io
github: gofiber/fiber
year: 2020
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, go, performance, express-like, api, rest, fasthttp]
related_frameworks: [gin, echo, chi]
features:
  - "Built on Fasthttp — fastest Go HTTP implementation, not net/http"
  - "Express-like API — routes, middleware, and context will feel familiar"
  - "Zero memory allocation routing for maximum throughput"
  - "Middleware: Logger, Limiter, Cache, CORS, JWT, Session"
  - "WebSocket and SSE support"
  - "Template engine support — HTML, Handlebars, Pug"
  - "File upload handling and static file serving"
  - "Prefork mode — spawn one worker per CPU core for maximum concurrency"
install:
  go: "go get github.com/gofiber/fiber/v2"
---

Fiber uses Fasthttp instead of `net/http` and is consistently one of the fastest web frameworks in any language. Its Express-inspired API helps Node.js developers transition to Go without a steep learning curve. Zero memory allocation routing and low-level tuning options make it ideal for high-throughput microservices. The trade-off is incompatibility with the `net/http` ecosystem — existing `http.Handler` middleware won't work.

## Quick start

```bash
go mod init my-api
go get github.com/gofiber/fiber/v2
```

```go
// main.go
package main

import (
	"github.com/gofiber/fiber/v2"
	"github.com/gofiber/fiber/v2/middleware/logger"
	"github.com/gofiber/fiber/v2/middleware/recover"
)

type Post struct {
	ID    int    `json:"id"`
	Title string `json:"title"`
	Body  string `json:"body"`
}

func main() {
	app := fiber.New()

	app.Use(logger.New())
	app.Use(recover.New())

	posts := []Post{}

	app.Get("/posts", func(c *fiber.Ctx) error {
		return c.JSON(posts)
	})

	app.Post("/posts", func(c *fiber.Ctx) error {
		var p Post
		if err := c.BodyParser(&p); err != nil {
			return c.Status(400).JSON(fiber.Map{"error": err.Error()})
		}
		p.ID = len(posts) + 1
		posts = append(posts, p)
		return c.Status(201).JSON(p)
	})

	app.Get("/posts/:id", func(c *fiber.Ctx) error {
		return c.JSON(fiber.Map{"id": c.Params("id")})
	})

	app.Listen(":3000")
}
```

## When to use

Fiber is ideal for Go microservices where raw throughput is the primary concern and you don't need to interop with `net/http` middleware. Its Express-like API makes it the gentlest transition for developers coming from Node.js. If you need to reuse existing `net/http` handlers or middleware, use Gin or Chi instead. For new high-throughput Go services where the `net/http` ecosystem is not a factor, Fiber delivers the best performance.
