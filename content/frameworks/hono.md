---
name: Hono
slug: hono
language: typescript
description: Ultrafast web framework for the edge — runs on Cloudflare Workers, Deno, Bun, Node.js, and AWS Lambda with zero dependencies.
logo: https://hono.dev/images/logo.svg
website: https://hono.dev
github: honojs/hono
year: 2021
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, edge, cloudflare, deno, bun, api, rest, typescript]
related_frameworks: [fastify, express, itty-router]
features:
  - "Runs on Cloudflare Workers, Deno Deploy, Bun, Node.js, and AWS Lambda"
  - "Trie-based router — one of the fastest route matchers available"
  - "Zero external dependencies — works in any JS runtime"
  - "Hono RPC — auto-generated type-safe client from your server routes"
  - "Built-in middleware: Bearer auth, CORS, logger, cache, compress"
  - "JSX support for server-side HTML rendering without React"
  - "TypeScript-first with fully typed request/response objects"
  - "Tiny bundle size — ideal for edge cold-start latency"
install:
  npm: "npm create hono@latest my-app"
  bun: "bun create hono my-app"
---

Hono is designed for the modern edge runtime landscape — the same code runs on Cloudflare Workers, Deno Deploy, Bun, and Node.js. Its trie-based router is among the fastest available, and full TypeScript support with RPC-style client generation makes end-to-end type safety straightforward. Its minimal footprint and zero dependencies make it particularly suited for Cloudflare Workers where cold starts are sensitive to bundle size.

## Quick start

```bash
npm create hono@latest my-app
# Select: Cloudflare Workers (or Node.js / Bun)
cd my-app && npm install && npm run dev
```

```typescript
// src/index.ts
import { Hono } from 'hono'
import { cors } from 'hono/cors'
import { logger } from 'hono/logger'

type Post = { id: number; title: string; body: string }

const app = new Hono()
const posts: Post[] = []

app.use('*', logger())
app.use('/api/*', cors())

app.get('/api/posts', (c) => c.json(posts))

app.post('/api/posts', async (c) => {
  const body = await c.req.json<Omit<Post, 'id'>>()
  const post = { id: posts.length + 1, ...body }
  posts.push(post)
  return c.json(post, 201)
})

app.get('/api/posts/:id', (c) => {
  const id = Number(c.req.param('id'))
  const post = posts.find(p => p.id === id)
  return post ? c.json(post) : c.json({ error: 'Not found' }, 404)
})

export default app
```

## When to use

Hono is the best choice for APIs deployed to edge runtimes (Cloudflare Workers, Deno Deploy) where bundle size and cold-start time are critical. Its universal runtime support means one codebase targets all JS environments. For Node.js-only projects, Express or Fastify have larger ecosystems. Hono's RPC layer is particularly compelling when you want Next.js-like end-to-end type safety without a full framework.
