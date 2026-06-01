---
name: Vue
slug: vue
language: javascript
description: Progressive JavaScript framework for building UIs — approachable, flexible, and incrementally adoptable.
logo: https://upload.wikimedia.org/wikipedia/commons/9/95/Vue.js_Logo_2.svg
website: https://vuejs.org
github: vuejs/core
year: 2014
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [ui, frontend, spa, sfc, components, progressive]
related_frameworks: [react, nuxt, svelte]
features:
  - "Single File Components (.vue) — template, script, and styles in one file"
  - "Composition API with `<script setup>` for clean, reusable logic"
  - "Reactive system — `ref()` and `reactive()` for fine-grained reactivity"
  - "Progressive adoption — drop a `<script>` tag or build a full SPA"
  - "Scoped CSS, CSS Modules, and CSS-in-JS all supported"
  - "Built-in transitions and animation system"
  - "Official ecosystem: Vue Router, Pinia (state), Vite (build tool)"
  - "TypeScript support built in — no extra config needed"
install:
  npm: "npm create vue@latest my-app"
  yarn: "yarn create vue my-app"
  pnpm: "pnpm create vue my-app"
---

Vue's single-file components and progressive adoption model make it a popular choice for teams wanting a gentler learning curve than React, with more structure than Svelte. The Composition API introduced in Vue 3 brings reactive primitives (`ref`, `reactive`, `computed`, `watch`) that compose cleanly into reusable logic, while `<script setup>` eliminates boilerplate. For full-stack Vue apps, Nuxt is the equivalent of Next.js.

## Quick start

```bash
npm create vue@latest my-app
# Select: TypeScript? Yes, Vue Router? Yes, Pinia? Yes
cd my-app && npm install && npm run dev
```

```vue
<!-- src/components/Counter.vue -->
<script setup lang="ts">
import { ref, computed } from 'vue'

const count = ref(0)
const doubled = computed(() => count.value * 2)

function increment() {
  count.value++
}
</script>

<template>
  <div class="counter">
    <p>Count: {{ count }} (doubled: {{ doubled }})</p>
    <button @click="increment">Increment</button>
  </div>
</template>

<style scoped>
.counter {
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
}
</style>
```

```vue
<!-- Fetch data with Composition API -->
<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface User { id: number; name: string }

const users = ref<User[]>([])

onMounted(async () => {
  const res = await fetch('/api/users')
  users.value = await res.json()
})
</script>

<template>
  <ul>
    <li v-for="user in users" :key="user.id">{{ user.name }}</li>
  </ul>
</template>
```

## When to use

Vue is a strong choice when you want React-like component architecture with a gentler onboarding curve and more built-in conveniences. It's particularly popular in Asia, in Laravel applications (via Inertia.js), and for teams migrating from jQuery who want a gradual path. For server-rendered Vue apps, Nuxt is the production standard.
