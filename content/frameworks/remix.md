---
name: Remix
slug: remix
language: typescript
description: Full-stack React framework built on web standards — loaders, actions, and nested routing with progressive enhancement.
logo: https://upload.wikimedia.org/wikipedia/commons/a/af/Remix.run_logo_wordmark.svg
website: https://remix.run
github: remix-run/remix
year: 2021
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [fullstack, react, ssr, web-standards, routing, typescript]
related_frameworks: [nextjs, react, sveltekit, astro]
features:
  - "Loaders for server-side data fetching co-located with each route"
  - "Actions for server-side form handling and mutations"
  - "Nested routing — parent routes wrap children, each with their own data"
  - "Progressive enhancement — works without JavaScript, enhances with it"
  - "Built on web standards — `Request`, `Response`, `FormData`, `fetch`"
  - "Optimistic UI with `useFetcher` and `useNavigation`"
  - "Error boundaries and `CatchBoundary` per route"
  - "Works on Node.js, Cloudflare Workers, Deno, and more"
install:
  npm: "npx create-remix@latest my-app"
  pnpm: "pnpm create remix my-app"
---

Remix embraces web platform primitives — HTML forms, HTTP caching, and Response/Request APIs — so apps work without JavaScript and progressively enhance. Its nested routing model co-locates data loading with UI components, and every route can define its own loader and action for server-side data fetching and mutations. Remix merged with React Router in 2024 and React Router v7 is now the successor.

## Quick start

```bash
npx create-remix@latest my-app
cd my-app && npm run dev
```

```tsx
// app/routes/posts._index.tsx — list route with loader
import { json } from '@remix-run/node'
import { useLoaderData, Link } from '@remix-run/react'
import type { LoaderFunctionArgs } from '@remix-run/node'

type Post = { id: number; title: string }

export async function loader({ request }: LoaderFunctionArgs) {
  const posts = await fetchPosts()
  return json({ posts })
}

export default function PostsIndex() {
  const { posts } = useLoaderData<typeof loader>()
  return (
    <main>
      <h1>Posts</h1>
      <ul>
        {posts.map(post => (
          <li key={post.id}><Link to={String(post.id)}>{post.title}</Link></li>
        ))}
      </ul>
    </main>
  )
}
```

```tsx
// app/routes/posts.new.tsx — form with action
import { redirect } from '@remix-run/node'
import { Form, useActionData } from '@remix-run/react'
import type { ActionFunctionArgs } from '@remix-run/node'

export async function action({ request }: ActionFunctionArgs) {
  const formData = await request.formData()
  const title = String(formData.get('title'))
  if (!title) return { error: 'Title is required' }
  await createPost({ title })
  return redirect('/posts')
}

export default function NewPost() {
  const actionData = useActionData<typeof action>()
  return (
    <Form method="post">
      <input name="title" placeholder="Title" />
      {actionData?.error && <p>{actionData.error}</p>}
      <button type="submit">Create</button>
    </Form>
  )
}
```

## When to use

Remix is ideal when you want server-rendered React with a strong emphasis on web standards and progressive enhancement — forms that work without JS, HTTP-level caching, and minimal client JS. Its nested routing is particularly elegant for complex UIs with multiple data sources. Next.js has a larger ecosystem and more deployment options. Remix's React Router v7 merger means the two projects are converging; React Router v7 is now the recommended entry point.
