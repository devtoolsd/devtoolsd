---
name: Tailwind CSS
slug: tailwindcss
language: javascript
description: Utility-first CSS framework — compose designs directly in markup with small, single-purpose classes.
logo: https://upload.wikimedia.org/wikipedia/commons/d/d5/Tailwind_CSS_Logo.svg
website: https://tailwindcss.com
github: tailwindlabs/tailwindcss
year: 2017
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [css, frontend, utility-first, styling, ui, design-system]
related_frameworks: [bootstrap]
features:
  - "Utility-first — no custom CSS needed, compose from single-purpose classes"
  - "Design tokens — colors, spacing, typography from a consistent scale"
  - "Responsive variants — `md:flex`, `lg:grid`, `xl:hidden`"
  - "Dark mode — `dark:bg-gray-800` with `class` or `media` strategy"
  - "Arbitrary values — `w-[37px]`, `text-[#1da1f2]` for one-off values"
  - "JIT engine purges unused classes — tiny CSS in production"
  - "Tailwind v4 rewritten in Rust — instant builds via Lightning CSS"
  - "shadcn/ui, Headless UI, and Radix UI complement it with accessible components"
install:
  npm: "npm install tailwindcss @tailwindcss/vite"
  cdn: '<script src="https://cdn.tailwindcss.com"></script>'
---

Tailwind replaces hand-written CSS with composable utility classes — `flex`, `pt-4`, `text-center`, `bg-blue-500` — applied directly in HTML. Its JIT engine removes unused classes in production, often resulting in smaller stylesheets than traditional approaches. Tailwind v4 rewrites the engine in Rust for near-instant builds and integrates directly with Vite via a plugin.

## Quick start

```bash
# Vite project
npm install tailwindcss @tailwindcss/vite
```

```javascript
// vite.config.js
import tailwindcss from '@tailwindcss/vite'
export default { plugins: [tailwindcss()] }
```

```css
/* src/index.css */
@import "tailwindcss";
```

```html
<!-- Example component -->
<div class="min-h-screen bg-gray-50 flex items-center justify-center">
  <div class="bg-white rounded-2xl shadow-lg p-8 max-w-md w-full">
    <h1 class="text-2xl font-bold text-gray-900 mb-2">Hello Tailwind</h1>
    <p class="text-gray-500 mb-6">Utility-first CSS for rapid UI development.</p>

    <div class="flex gap-3">
      <button class="bg-blue-600 hover:bg-blue-700 text-white font-medium
                     px-4 py-2 rounded-lg transition-colors">
        Primary
      </button>
      <button class="border border-gray-300 hover:border-gray-400 text-gray-700
                     font-medium px-4 py-2 rounded-lg transition-colors">
        Secondary
      </button>
    </div>

    <!-- Responsive grid -->
    <div class="mt-6 grid grid-cols-1 sm:grid-cols-2 gap-4">
      <div class="p-4 bg-gray-50 rounded-lg">
        <p class="text-sm font-medium text-gray-900">Card 1</p>
      </div>
      <div class="p-4 bg-gray-50 rounded-lg">
        <p class="text-sm font-medium text-gray-900">Card 2</p>
      </div>
    </div>
  </div>
</div>
```

## When to use

Tailwind is the best choice for projects where you want a design system with constraints (spacing scale, color palette, typography) without writing CSS files. It's particularly efficient in component-based frameworks (React, Vue, Svelte) where utility classes stay co-located with the component. Bootstrap is better when you want pre-built components with minimal setup. For design systems that need consistent, accessible UI components on top of Tailwind, shadcn/ui or Radix UI are the recommended additions.
