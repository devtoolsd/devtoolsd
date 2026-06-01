---
name: Fastify
slug: fastify
language: javascript
description: High-performance Node.js web framework — schema-based validation, plugin architecture, and up to 2x the throughput of Express.
logo: https://upload.wikimedia.org/wikipedia/commons/a/ab/Fastify_logo.svg
website: https://fastify.dev
github: fastify/fastify
year: 2016
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, nodejs, api, rest, performance, schema, plugins]
related_frameworks: [express, koa, nestjs, hono]
features:
  - "JSON Schema validation for inputs and outputs — faster serialization than JSON.stringify"
  - "Plugin architecture with dependency injection and encapsulation"
  - "Up to 2× the throughput of Express at comparable configurations"
  - "Full TypeScript support with auto-generated types from schemas"
  - "Built-in OpenAPI/Swagger plugin (`@fastify/swagger`)"
  - "Lifecycle hooks — `onRequest`, `preHandler`, `onSend`, and more"
  - "Async/await native — no callback pyramid of doom"
  - "Drop-in compatibility with many Express middleware via `@fastify/express`"
install:
  npm: "npm install fastify"
  yarn: "yarn add fastify"
  pnpm: "pnpm add fastify"
---

Fastify's JSON schema validation pipeline and low overhead make it one of the fastest Node.js frameworks available. Its plugin system with automatic dependency injection ensures encapsulation and reuse across large applications. Full TypeScript support and a Swagger plugin make it popular for building typed, self-documenting APIs. It's the recommended replacement for Express when performance matters.

## Quick start

```bash
npm install fastify
```

```javascript
// server.js
import Fastify from 'fastify'

const app = Fastify({ logger: true })

const postSchema = {
  body: {
    type: 'object',
    required: ['title', 'body'],
    properties: {
      title: { type: 'string' },
      body: { type: 'string' },
    },
  },
  response: {
    201: {
      type: 'object',
      properties: {
        id: { type: 'integer' },
        title: { type: 'string' },
        body: { type: 'string' },
      },
    },
  },
}

const posts = []

app.get('/posts', async () => posts)

app.post('/posts', { schema: postSchema }, async (request, reply) => {
  const post = { id: posts.length + 1, ...request.body }
  posts.push(post)
  return reply.code(201).send(post)
})

await app.listen({ port: 3000 })
```

## When to use

Fastify is the best drop-in upgrade from Express when you need better performance and built-in schema validation. Its plugin system scales better than Express middleware for large applications. For teams using TypeScript, Fastify's schema-to-type generation reduces boilerplate significantly. If you're starting fresh and want even more structure, NestJS can run on Fastify underneath. For edge/serverless environments, Hono is even lighter.
