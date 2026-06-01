---
name: Solid
slug: solid
language: javascript
description: Fine-grained reactive UI library — no virtual DOM, JSX compiled to real DOM operations, with React-like ergonomics.
website: https://solidjs.com
github: solidjs/solid
year: 2018
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [frontend, reactive, jsx, performance, spa, ui, fine-grained]
related_frameworks: [react, svelte, vue, qwik]
features:
  - "No virtual DOM — JSX compiles to direct DOM operations"
  - "Fine-grained reactivity — only the affected DOM nodes update"
  - "Signals as primitives — `createSignal`, `createEffect`, `createMemo`"
  - "Consistent JSX that mirrors React conventions"
  - "Components are just functions — no re-render lifecycle, run once"
  - "Built-in control flow: `<Show>`, `<For>`, `<Switch>`, `<Suspense>`"
  - "Stores for complex state — `createStore` with nested reactivity"
  - "SolidStart — full-stack meta-framework with SSR and file-based routing"
install:
  npm: "npm create solid@latest my-app"
  pnpm: "pnpm create solid my-app"
---

Solid's reactive primitives — signals, effects, and memos — update only the exact DOM nodes that change, with no diffing overhead. It uses JSX like React but compiles it to direct DOM operations. Components run once (not on every render), making mental models simpler once you understand signals. Solid consistently ranks as one of the fastest UI frameworks while providing a familiar development model for React developers.

## Quick start

```bash
npm create solid@latest my-app
cd my-app && npm install && npm run dev
```

```tsx
// src/components/Counter.tsx
import { createSignal, createMemo, Show } from 'solid-js'

function Counter() {
  const [count, setCount] = createSignal(0)
  const doubled = createMemo(() => count() * 2)

  return (
    <div>
      <p>Count: {count()}</p>
      <p>Doubled: {doubled()}</p>
      <button onClick={() => setCount(c => c + 1)}>Increment</button>
      <Show when={count() > 5}>
        <p>Count is greater than 5!</p>
      </Show>
    </div>
  )
}

export default Counter
```

```tsx
// src/components/UserList.tsx
import { createResource, For, Suspense } from 'solid-js'

type User = { id: number; name: string }

async function fetchUsers(): Promise<User[]> {
  const res = await fetch('/api/users')
  return res.json()
}

function UserList() {
  const [users] = createResource(fetchUsers)

  return (
    <Suspense fallback={<p>Loading...</p>}>
      <ul>
        <For each={users()}>
          {user => <li>{user.name}</li>}
        </For>
      </ul>
    </Suspense>
  )
}
```

## When to use

Solid is the best choice when you want React-like JSX and component patterns with significantly better performance and smaller bundle size. It's ideal for performance-sensitive UIs and for teams comfortable with signals-based reactivity. The trade-off is a smaller ecosystem than React and Vue. For full-stack applications, SolidStart provides SSR and file-based routing. If your team is deeply invested in React's ecosystem (libraries, patterns), the performance gains may not justify the migration cost.
