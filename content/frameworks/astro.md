---
name: Astro
slug: astro
language: typescript
description: Content-focused web framework with islands architecture — ships zero JavaScript by default, integrates any UI framework.
logo: https://upload.wikimedia.org/wikipedia/commons/8/80/Wordpress_Astro_-_Full_Logo_Light_Color_%281%29.svg
website: https://astro.build
github: withastro/astro
year: 2021
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [frontend, static, ssr, performance, islands, content, multi-framework]
related_frameworks: [nextjs, remix, sveltekit, gatsby]
features:
  - "Islands architecture — ship zero JavaScript by default, hydrate only what's interactive"
  - "Framework-agnostic — use React, Vue, Svelte, Solid, or Preact in the same project"
  - "Content Collections with typed schemas for markdown and MDX"
  - "File-based routing with static, SSR, and hybrid rendering per page"
  - "View Transitions API for smooth page animations"
  - "Astro DB — built-in SQLite database for content apps"
  - "Image component with automatic optimisation and lazy loading"
  - "Deploy to Vercel, Netlify, Cloudflare, Node.js, or static CDN"
install:
  npm: "npm create astro@latest"
  pnpm: "pnpm create astro@latest"
---

Astro's islands architecture renders pages as static HTML and hydrates only the interactive components that need JavaScript. It is framework-agnostic — you can mix React, Vue, Svelte, and Solid components in the same project. Content Collections with typed schemas make it the ideal choice for documentation sites, blogs, and marketing pages. Astro 4 added the View Transitions API and Astro DB for simple data persistence.

## Quick start

```bash
npm create astro@latest my-site
cd my-site && npm run dev
```

```astro
---
// src/pages/index.astro
import { getCollection } from 'astro:content'
import Layout from '../layouts/Layout.astro'
import Counter from '../components/Counter.jsx' // React island

const posts = await getCollection('blog')
---

<Layout title="My Blog">
  <h1>Latest Posts</h1>
  <ul>
    {posts.map(post => (
      <li>
        <a href={`/blog/${post.slug}`}>{post.data.title}</a>
      </li>
    ))}
  </ul>

  <!-- Only this component ships JavaScript -->
  <Counter client:load />
</Layout>
```

```typescript
// src/content/config.ts
import { z, defineCollection } from 'astro:content'

const blog = defineCollection({
  schema: z.object({
    title: z.string(),
    date: z.date(),
    tags: z.array(z.string()).optional(),
  }),
})

export const collections = { blog }
```

## When to use

Astro is the best choice for content-heavy sites — documentation, blogs, marketing sites, and portfolios — where JavaScript payload must be minimal. Its island architecture means interactive widgets only ship JS for those components, not the whole page. For highly interactive SPAs (dashboards, apps), Next.js or SvelteKit are more appropriate. If you need CMS integration, Astro's Content Collections or headless CMS adapters (Contentful, Sanity) work seamlessly.
