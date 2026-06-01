---
name: SvelteKit
slug: sveltekit
language: javascript
description: Full-stack Svelte framework with SSR, file-based routing, and edge-ready deployment — the official way to build Svelte apps.
logo: https://upload.wikimedia.org/wikipedia/commons/1/1b/Svelte_Logo.svg
website: https://kit.svelte.dev
github: sveltejs/kit
year: 2020
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [fullstack, ssr, routing, svelte, edge, deployment]
related_frameworks: [svelte, nextjs, nuxt, remix]
features:
  - "File-based routing — `src/routes/blog/[slug]/+page.svelte` is `/blog/:slug`"
  - "`load()` functions for server-side and client-side data fetching"
  - "Form Actions — handle form submissions server-side with progressive enhancement"
  - "Adapters for Vercel, Netlify, Cloudflare Workers, Node.js, and static sites"
  - "Server routes via `+server.ts` for API endpoints alongside pages"
  - "Layout files and error boundaries built into the routing system"
  - "Streaming and deferred loading for fast initial page renders"
  - "Type-safe route parameters and load function return types"
install:
  npm: "npm create svelte@latest my-app"
  pnpm: "pnpm create svelte my-app"
---

SvelteKit is to Svelte what Next.js is to React — a full-stack framework with file-based routing, server-side rendering, form actions, and adapters for every major deployment target. Its `+page.server.ts` convention cleanly separates server and client code while keeping them co-located by route. The adapter system means the same codebase deploys to Node.js, Vercel Edge, Cloudflare Workers, or a static CDN.

## Quick start

```bash
npm create svelte@latest my-app
# Select: SvelteKit demo app, TypeScript, ESLint + Prettier
cd my-app && npm install && npm run dev
```

```
src/routes/
  +layout.svelte          # shared layout for all pages
  +page.svelte            # homepage
  blog/
    +page.svelte          # /blog listing
    +page.server.ts       # server load function for /blog
    [slug]/
      +page.svelte        # /blog/:slug
      +page.server.ts     # load post by slug on the server
```

```typescript
// src/routes/blog/[slug]/+page.server.ts
import { error } from '@sveltejs/kit'
import type { PageServerLoad } from './$types'

export const load: PageServerLoad = async ({ params }) => {
  const post = await fetchPost(params.slug)
  if (!post) throw error(404, 'Post not found')
  return { post }
}
```

```svelte
<!-- src/routes/blog/[slug]/+page.svelte -->
<script lang="ts">
  import type { PageData } from './$types'
  let { data }: { data: PageData } = $props()
</script>

<article>
  <h1>{data.post.title}</h1>
  <div>{@html data.post.content}</div>
</article>
```

## When to use

SvelteKit is the right choice for any Svelte application that needs server rendering, routing, or API endpoints — which is most production apps. Use bare Svelte only for isolated widgets or when embedding into an existing non-Svelte site. For teams comfortable with React, Next.js offers a larger ecosystem. SvelteKit's edge-deployment story via Cloudflare Workers adapter is particularly strong for globally distributed apps.
