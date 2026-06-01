---
name: Express
slug: express
language: javascript
description: Minimal, unopinionated Node.js web framework — the backbone of most Node.js APIs and servers.
logo: https://upload.wikimedia.org/wikipedia/commons/6/64/Expressjs.png
website: https://expressjs.com
github: expressjs/express
year: 2010
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [nodejs, backend, api, rest, middleware, server]
related_frameworks: [fastify, koa, nestjs]
features:
  - "Minimal and unopinionated — bring your own structure and libraries"
  - "Robust middleware system using `app.use()` for logging, auth, parsing"
  - "Simple and expressive routing with params, wildcards, and chaining"
  - "Supports template engines (EJS, Pug, Handlebars)"
  - "Huge ecosystem — thousands of middleware packages on npm"
  - "HTTP helpers for requests, responses, and status codes"
  - "Easily compose sub-routers for modular application structure"
  - "Works with any Node.js database driver or ORM"
install:
  npm: "npm install express"
  yarn: "yarn add express"
  pnpm: "pnpm add express"
---

Express is the minimal, flexible Node.js web application framework that set the template for how JavaScript servers are built. Its middleware model — a chain of functions that process an HTTP request — is so intuitive that nearly every other Node.js framework (Koa, Fastify, Hono) adopted the same concept. It doesn't prescribe project structure, ORM, or validation library, making it a foundation you can shape to any use case.

## Quick start

```bash
npm init -y
npm install express
```

```js
// server.js
const express = require('express')
const app = express()

// Parse JSON request bodies
app.use(express.json())

// Route handlers
app.get('/', (req, res) => {
  res.json({ message: 'Hello from Express' })
})

app.get('/users/:id', (req, res) => {
  res.json({ id: req.params.id })
})

app.post('/users', (req, res) => {
  const { name, email } = req.body
  // ... save to database
  res.status(201).json({ name, email })
})

// Custom middleware
app.use((err, req, res, next) => {
  console.error(err.stack)
  res.status(500).json({ error: 'Something went wrong' })
})

app.listen(3000, () => console.log('Server running on port 3000'))
```

## When to use

Express is the safe default for Node.js HTTP servers and REST APIs — it's battle-tested, well-documented, and every Node.js developer knows it. Choose it when you want full control and a proven ecosystem. If raw performance is critical, Fastify is a faster drop-in replacement with the same middleware concept. For large, structured TypeScript applications, NestJS provides opinionated architecture on top of Express.
