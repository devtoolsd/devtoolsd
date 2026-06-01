---
name: Koa
slug: koa
language: javascript
description: Next-generation Node.js web framework from the Express team — async/await middleware pipeline, minimal core.
website: https://koajs.com
github: koajs/koa
year: 2013
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, nodejs, api, middleware, async, minimal]
related_frameworks: [express, fastify, hono]
features:
  - "Async middleware cascade — `await next()` replaces callback chains"
  - "Upstream/downstream middleware flow — execute code after `next()`"
  - "`ctx` context object combining `req` and `res` into one clean API"
  - "No bundled routing — bring your own (koa-router, @koa/router)"
  - "Error handling via try/catch anywhere in the middleware chain"
  - "Lightweight core — less than 600 lines of source"
  - "Streaming support and native HTTP/2 compatibility"
  - "Large ecosystem of Koa-compatible middleware"
install:
  npm: "npm install koa"
  yarn: "yarn add koa"
  pnpm: "pnpm add koa"
---

Koa was built by the Express team to address its callback-based design — its async middleware cascade uses `async/await` natively and avoids callback hell. The "onion model" means middleware executes code before and after `await next()`, making it easy to implement request logging, error handling, and response transformation cleanly. With no bundled routing or templates, Koa is a thin foundation that teams assemble with their own middleware stack.

## Quick start

```bash
npm install koa @koa/router koa-bodyparser
```

```javascript
// server.js
const Koa = require('koa')
const Router = require('@koa/router')
const bodyParser = require('koa-bodyparser')

const app = new Koa()
const router = new Router()

const posts = []

// Middleware: logging
app.use(async (ctx, next) => {
  const start = Date.now()
  await next()
  console.log(`${ctx.method} ${ctx.url} - ${Date.now() - start}ms`)
})

// Middleware: error handling
app.use(async (ctx, next) => {
  try {
    await next()
  } catch (err) {
    ctx.status = err.status || 500
    ctx.body = { error: err.message }
  }
})

router.get('/posts', (ctx) => {
  ctx.body = posts
})

router.post('/posts', (ctx) => {
  const post = { id: posts.length + 1, ...ctx.request.body }
  posts.push(post)
  ctx.status = 201
  ctx.body = post
})

app.use(bodyParser())
app.use(router.routes())
app.use(router.allowedMethods())

app.listen(3000, () => console.log('Server on :3000'))
```

## When to use

Koa is a good choice when you want a cleaner async API than Express with full control over your middleware stack, but don't need the structured approach of NestJS or the schema validation of Fastify. Its small core is well-suited for teams that want to compose their own framework from smaller packages. For most new projects, Fastify's schema validation and performance or Hono's edge-runtime support are stronger starting points.
