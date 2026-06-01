---
name: Nuxt
slug: nuxt
language: typescript
description: Full-stack Vue framework with SSR, file-based routing, and auto-imports — the standard way to build production Vue apps.
logo: https://upload.wikimedia.org/wikipedia/commons/a/ae/Nuxt_logo.svg
website: https://nuxt.com
github: nuxt/nuxt
year: 2016
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [fullstack, vue, ssr, typescript, routing, auto-imports]
related_frameworks: [vue, nextjs, sveltekit, remix]
features:
  - "File-based routing — `pages/blog/[slug].vue` becomes `/blog/:slug`"
  - "Auto-imports for components, composables, and Vue APIs — no import statements"
  - "Server-side rendering, static generation, and hybrid rendering per route"
  - "Nitro server engine — deploys to Node.js, Vercel Edge, Cloudflare Workers"
  - "Nuxt modules ecosystem — Nuxt Image, Content, Auth, and 200+ modules"
  - "Nuxt Content for markdown-based pages and blog posts"
  - "Server API routes via `server/api/` directory"
  - "TypeScript-first with auto-generated route types"
install:
  npm: "npx nuxi@latest init my-app"
  pnpm: "pnpm dlx nuxi@latest init my-app"
---

Nuxt provides a complete application framework on top of Vue — server-side rendering, static generation, file-based routing, auto-imported components, and composables. Nuxt 3 is built on Nitro (a universal server runtime) and Vite, enabling deployment to Node.js, edge functions, and serverless environments. Its auto-import system means you can use `ref`, `useState`, and your own composables anywhere without explicit imports.

## Quick start

```bash
npx nuxi@latest init my-app
cd my-app && npm install && npm run dev
```

```
pages/
  index.vue          # route: /
  blog/
    index.vue        # route: /blog
    [slug].vue       # route: /blog/:slug
server/
  api/
    posts.get.ts     # GET /api/posts
    posts/[id].get.ts
```

```vue
<!-- pages/blog/[slug].vue -->
<script setup lang="ts">
const route = useRoute()
const { data: post } = await useFetch(`/api/posts/${route.params.slug}`)
</script>

<template>
  <article v-if="post">
    <h1>{{ post.title }}</h1>
    <p>{{ post.body }}</p>
  </article>
</template>
```

```typescript
// server/api/posts.get.ts
export default defineEventHandler(async () => {
  return [
    { id: 1, title: 'Hello Nuxt', body: 'Getting started with Nuxt 3.' }
  ]
})
```

## When to use

Nuxt is the standard choice for production Vue applications. Its SSR and static generation capabilities make it ideal for content-heavy sites, e-commerce, and SEO-sensitive applications. If your stack is already Vue-based, Nuxt adds the server layer without friction. For React teams, Next.js is the equivalent. Nuxt's module ecosystem is particularly strong — if you need auth, i18n, or image optimisation, there's a first-class module for it.
