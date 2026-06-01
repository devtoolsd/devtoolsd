---
name: Svelte
slug: svelte
language: javascript
description: Compiler-based UI framework — no virtual DOM, components compile to vanilla JS for minimal bundle size and maximum performance.
logo: https://upload.wikimedia.org/wikipedia/commons/1/1b/Svelte_Logo.svg
website: https://svelte.dev
github: sveltejs/svelte
year: 2016
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [frontend, components, compiler, performance, spa, ui]
related_frameworks: [sveltekit, react, vue, solid]
features:
  - "Compiler-based — components compile to optimised vanilla JS, no runtime overhead"
  - "No virtual DOM — direct DOM mutations for maximum performance"
  - "Reactive assignments — `count++` just works, no `useState` or `ref()` needed"
  - "Scoped CSS built into every component by default"
  - "Stores for shared state — `writable()`, `readable()`, `derived()`"
  - "Transitions and animations as first-class language features"
  - "Svelte 5 Runes — `$state`, `$derived`, `$effect` for fine-grained reactivity"
  - "Smallest bundle sizes of any major UI framework"
install:
  npm: "npm create svelte@latest my-app"
  pnpm: "pnpm create svelte my-app"
---

Svelte shifts work from the browser to compile time — there's no runtime framework overhead, just optimised vanilla JavaScript. Its reactive assignments and simple syntax make it approachable for beginners while its performance characteristics appeal to production teams building fast, lightweight UIs. Svelte 5 introduced Runes (`$state`, `$derived`, `$effect`) as a more explicit reactivity system that also works outside of `.svelte` files.

## Quick start

```bash
npm create svelte@latest my-app
cd my-app && npm install && npm run dev
```

```svelte
<!-- src/lib/Counter.svelte -->
<script>
  let count = $state(0)
  const doubled = $derived(count * 2)
</script>

<button onclick={() => count++}>
  Count: {count} (doubled: {doubled})
</button>

<style>
  button {
    padding: 0.5rem 1rem;
    font-size: 1rem;
  }
</style>
```

```svelte
<!-- Fetch data with onMount -->
<script>
  import { onMount } from 'svelte'

  let users = []

  onMount(async () => {
    const res = await fetch('/api/users')
    users = await res.json()
  })
</script>

{#each users as user (user.id)}
  <p>{user.name}</p>
{/each}
```

## When to use

Svelte is the best choice when bundle size and runtime performance are priorities — marketing pages, interactive widgets embedded in larger sites, and performance-sensitive dashboards. Its simpler syntax lowers the barrier to entry compared to React or Vue. For a full-stack Svelte application with SSR and routing, use SvelteKit. The ecosystem is smaller than React's, so factor in library availability for complex UI requirements.
