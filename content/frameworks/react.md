---
name: React
slug: react
language: javascript
description: Declarative UI library from Meta for building component-based web interfaces.
logo: https://upload.wikimedia.org/wikipedia/commons/a/a7/React-icon.svg
website: https://react.dev
github: facebook/react
year: 2013
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [ui, frontend, spa, jsx, components, meta]
related_frameworks: [nextjs, vue, svelte]
features:
  - "Component-based architecture — build encapsulated pieces, compose them into complex UIs"
  - "Virtual DOM for efficient updates and reconciliation"
  - "JSX — write HTML-like syntax directly inside JavaScript"
  - "Hooks API — useState, useEffect, useContext, and custom hooks"
  - "Unidirectional data flow for predictable state management"
  - "Rich ecosystem — React Router, TanStack Query, Zustand, Redux"
  - "Server Components and Suspense for streaming and async rendering"
  - "React Native reuses the same component model for mobile apps"
install:
  npm: "npm create vite@latest my-app -- --template react"
  yarn: "yarn create vite my-app --template react"
  pnpm: "pnpm create vite my-app --template react"
---

React introduced the component model to mainstream frontend development and remains the most widely used UI library in the world. Its declarative approach — describe what the UI should look like for a given state and let React figure out the DOM updates — replaced the imperative jQuery era. React underpins Next.js, Remix, Gatsby, and Expo, giving it an enormous ecosystem of tooling, patterns, and community support.

## Quick start

```jsx
// src/App.jsx
import { useState } from 'react'

function Counter() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  )
}

function App() {
  return (
    <main>
      <h1>Hello React</h1>
      <Counter />
    </main>
  )
}

export default App
```

```jsx
// Fetch data with useEffect
import { useState, useEffect } from 'react'

function UserList() {
  const [users, setUsers] = useState([])

  useEffect(() => {
    fetch('/api/users')
      .then(res => res.json())
      .then(data => setUsers(data))
  }, [])

  return (
    <ul>
      {users.map(user => <li key={user.id}>{user.name}</li>)}
    </ul>
  )
}
```

## When to use

React is the default choice for interactive web UIs. Use it when your project needs a large ecosystem, long-term stability, and a wide hiring pool. For server-rendered or full-stack apps, reach for Next.js or Remix on top of React. If you want less boilerplate and a smaller bundle, Vue or Svelte are worth considering for greenfield projects.
