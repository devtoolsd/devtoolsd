---
name: Jest
slug: jest
language: javascript
description: Delightful JavaScript testing framework from Meta — zero config, snapshot testing, mocking, and code coverage built in.
logo: https://upload.wikimedia.org/wikipedia/commons/b/b0/NewJestLogo.png
website: https://jestjs.io
github: jestjs/jest
year: 2014
pricing: free
open_source: true
license: MIT
tool_type: testing
tags: [testing, unit-testing, javascript, typescript, mocking, snapshots, meta]
related_frameworks: [vitest, mocha, cypress]
features:
  - "Zero configuration — works out of the box with React, Node.js, TypeScript"
  - "Built-in mocking — `jest.fn()`, `jest.spyOn()`, auto-mock modules"
  - "Snapshot testing — assert that UI components don't change unexpectedly"
  - "Parallel test execution across worker threads"
  - "Built-in code coverage via V8 or Istanbul"
  - "Watch mode with smart test selection based on changed files"
  - "Rich assertion library via `expect()`"
  - "jsdom environment for DOM testing without a browser"
install:
  npm: "npm install --save-dev jest"
  yarn: "yarn add -D jest"
  pnpm: "pnpm add -D jest"
---

Jest is the dominant JavaScript testing framework — it runs tests in parallel in isolated environments, provides snapshot testing for UI components, and has a built-in mocking library. Its zero-configuration setup works with React, Vue, Node.js, and TypeScript out of the box. Vitest is a modern alternative that reuses Vite's build pipeline for faster runs in Vite-based projects.

## Quick start

```bash
npm install --save-dev jest
# For TypeScript
npm install --save-dev @types/jest ts-jest
```

```javascript
// math.js
function add(a, b) { return a + b }
function divide(a, b) {
  if (b === 0) throw new Error('Division by zero')
  return a / b
}
module.exports = { add, divide }
```

```javascript
// math.test.js
const { add, divide } = require('./math')

describe('add()', () => {
  test('returns sum of two numbers', () => {
    expect(add(2, 3)).toBe(5)
  })
  test('handles negative numbers', () => {
    expect(add(-1, 1)).toBe(0)
  })
})

describe('divide()', () => {
  test('divides two numbers', () => {
    expect(divide(10, 2)).toBe(5)
  })
  test('throws on division by zero', () => {
    expect(() => divide(5, 0)).toThrow('Division by zero')
  })
})
```

```javascript
// Mocking example
const fetchUser = jest.fn().mockResolvedValue({ id: 1, name: 'Alice' })

test('renders user name', async () => {
  const user = await fetchUser(1)
  expect(user.name).toBe('Alice')
  expect(fetchUser).toHaveBeenCalledWith(1)
})
```

```bash
npx jest          # run all tests
npx jest --watch  # watch mode
npx jest --coverage
```

## When to use

Jest is the default choice for JavaScript and TypeScript unit and integration tests. It's pre-configured in Create React App, Next.js, and most scaffolding tools. For Vite-based projects (SvelteKit, Astro, Vite React), Vitest is faster because it reuses the existing build pipeline. For end-to-end browser tests, Playwright or Cypress are more appropriate.
