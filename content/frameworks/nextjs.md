---
name: Next.js
slug: nextjs
language: javascript
description: React framework with file-based routing, SSR, SSG, and API routes — the standard for production React apps.
logo: https://upload.wikimedia.org/wikipedia/commons/8/8e/Nextjs-logo.svg
website: https://nextjs.org
github: vercel/next.js
year: 2016
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [react, ssr, ssg, full-stack, vercel, routing]
related_frameworks: [react, remix, nuxt]
features:
  - "File-based routing — create a file in `app/` and it becomes a route"
  - "Server Components by default — zero client JS unless you opt in"
  - "Static generation (SSG), server-side rendering (SSR), and ISR in one framework"
  - "Built-in API routes for backend logic alongside your UI"
  - "Image, Font, and Script components with automatic optimizations"
  - "Streaming and Suspense support for progressive page loading"
  - "Middleware for auth, redirects, and edge logic"
  - "Turbopack dev server for fast hot-module replacement"
install:
  npm: "npx create-next-app@latest my-app"
  yarn: "yarn create next-app my-app"
  pnpm: "pnpm create next-app my-app"
---

Next.js adds server-side rendering, static generation, file-based routing, and API routes on top of React. With the App Router (introduced in v13), every component is a React Server Component by default — HTML is generated on the server and only interactive islands ship JavaScript to the browser. It's the default choice for production React applications and is maintained by Vercel with active community contributions.

## Quick start

```bash
npx create-next-app@latest my-app --typescript --tailwind --app
cd my-app
npm run dev
```

```tsx
// app/page.tsx — Server Component (no 'use client')
export default async function HomePage() {
  const posts = await fetch('https://api.example.com/posts').then(r => r.json())

  return (
    <main>
      <h1>Blog</h1>
      <ul>
        {posts.map((post: { id: number; title: string }) => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </main>
  )
}

// app/posts/[slug]/page.tsx — dynamic route
export default function PostPage({ params }: { params: { slug: string } }) {
  return <h1>Post: {params.slug}</h1>
}

// app/api/hello/route.ts — API route
export async function GET() {
  return Response.json({ message: 'Hello from Next.js API' })
}
```

## When to use

Next.js is the right choice when you're building a React app and want routing, server rendering, and API routes without assembling them yourself. It excels for content sites, e-commerce, SaaS dashboards, and anything that benefits from fast initial page loads. For purely client-rendered SPAs with no SEO requirements, plain React with Vite is simpler. For a non-React alternative with equivalent features, see Nuxt (Vue) or SvelteKit.
