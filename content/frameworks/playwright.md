---
name: Playwright
slug: playwright
language: typescript
description: End-to-end browser testing framework from Microsoft — reliable, fast, and supports Chromium, Firefox, and WebKit.
logo: https://playwright.dev/img/playwright-logo.svg
website: https://playwright.dev
github: microsoft/playwright
year: 2020
pricing: free
open_source: true
license: Apache-2.0
tool_type: testing
tags: [testing, e2e, browser, automation, typescript, microsoft, cross-browser]
related_frameworks: [cypress, selenium]
features:
  - "Supports Chromium, Firefox, and WebKit (Safari engine) — one test suite"
  - "Auto-wait — no manual sleeps or waits for elements to be ready"
  - "Parallel test execution across workers and browsers"
  - "Codegen — record browser interactions and generate test code"
  - "Screenshots, videos, and trace viewer for debugging failures"
  - "API testing mode — test HTTP endpoints without a browser"
  - "Mobile viewport simulation for responsive testing"
  - "Playwright Test report with built-in retry and error analysis"
install:
  npm: "npm init playwright@latest"
  yarn: "yarn create playwright"
---

Playwright auto-waits for elements to be ready before interacting, eliminating flaky tests caused by timing issues. It supports parallel test execution across Chromium, Firefox, and WebKit — including mobile viewports. Its codegen tool records browser interactions and generates test code, making it accessible to non-programmers. The Trace Viewer provides a full timeline of test execution for debugging.

## Quick start

```bash
npm init playwright@latest
# Installs browsers, creates playwright.config.ts
npx playwright test
```

```typescript
// tests/posts.spec.ts
import { test, expect } from '@playwright/test'

test.describe('Posts page', () => {
  test.beforeEach(async ({ page }) => {
    await page.goto('/posts')
  })

  test('displays the post list', async ({ page }) => {
    await expect(page.getByRole('heading', { name: 'Posts' })).toBeVisible()
    await expect(page.locator('[data-testid="post-item"]')).toHaveCount(3)
  })

  test('navigates to a post', async ({ page }) => {
    await page.getByText('Hello Playwright').click()
    await expect(page).toHaveURL(/\/posts\/\d+/)
    await expect(page.getByRole('heading', { level: 1 })).toContainText('Hello Playwright')
  })

  test('creates a new post', async ({ page }) => {
    await page.getByRole('link', { name: 'New Post' }).click()
    await page.getByLabel('Title').fill('My New Post')
    await page.getByLabel('Body').fill('Post content here')
    await page.getByRole('button', { name: 'Submit' }).click()
    await expect(page.getByText('My New Post')).toBeVisible()
  })
})
```

```typescript
// API testing
test('POST /api/posts returns 201', async ({ request }) => {
  const response = await request.post('/api/posts', {
    data: { title: 'Test', body: 'Body' },
  })
  expect(response.status()).toBe(201)
  const body = await response.json()
  expect(body).toMatchObject({ title: 'Test' })
})
```

## When to use

Playwright is the best choice for end-to-end testing when you need cross-browser coverage (Chromium + Firefox + WebKit) or are testing at scale with parallel workers. Its API testing mode makes it useful for integration tests without a UI. Compared to Cypress, Playwright has a more powerful API for multi-tab and multi-page flows, but Cypress has a more polished interactive debugging experience for in-browser development. For projects already using Cypress, switching isn't necessary unless cross-browser coverage is needed.
