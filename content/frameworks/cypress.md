---
name: Cypress
slug: cypress
language: javascript
description: End-to-end and component testing framework for web apps — runs in-browser with real-time reloading and a time-travel debugger.
logo: https://asset.brandfetch.io/idIq_kJ0rb/idv3zwmSiY.jpeg
website: https://cypress.io
github: cypress-io/cypress
year: 2014
pricing: freemium
open_source: true
license: MIT
tool_type: testing
tags: [testing, e2e, browser, component-testing, javascript, debug, time-travel]
related_frameworks: [playwright, jest]
features:
  - "Runs inside the browser — no WebDriver, no network proxy overhead"
  - "Time-travel debugger — hover over test steps to see screenshots"
  - "Automatic waiting — no explicit `wait` calls needed"
  - "Real-time reload during test development"
  - "Component testing for React, Vue, Svelte, and Angular in isolation"
  - "Network request interception via `cy.intercept()`"
  - "Video recording and screenshots on CI failure"
  - "Cypress Studio for recording tests by clicking through the UI"
install:
  npm: "npm install --save-dev cypress"
  yarn: "yarn add -D cypress"
  pnpm: "pnpm add -D cypress"
---

Cypress runs directly inside the browser alongside the application under test — no WebDriver, no network latency. Its time-travel debugger lets you hover over each test step and see what the browser looked like at that moment. Cypress Component Testing extends it to isolated component-level testing without a full browser environment. The developer experience (fast feedback, descriptive errors, automatic waits) set a new standard for frontend testing tools.

## Quick start

```bash
npm install --save-dev cypress
npx cypress open
```

```javascript
// cypress/e2e/posts.cy.js
describe('Posts page', () => {
  beforeEach(() => {
    // Stub the API so tests don't need a real backend
    cy.intercept('GET', '/api/posts', [
      { id: 1, title: 'Hello Cypress', body: 'Testing made easy.' }
    ]).as('getPosts')

    cy.visit('/posts')
    cy.wait('@getPosts')
  })

  it('displays a list of posts', () => {
    cy.get('[data-testid="post-item"]').should('have.length', 1)
    cy.contains('Hello Cypress')
  })

  it('navigates to a post on click', () => {
    cy.get('[data-testid="post-item"]').first().click()
    cy.url().should('include', '/posts/1')
    cy.get('h1').should('contain', 'Hello Cypress')
  })

  it('submits a new post form', () => {
    cy.intercept('POST', '/api/posts', { id: 2, title: 'New Post' }).as('createPost')
    cy.get('[data-testid="new-post-btn"]').click()
    cy.get('input[name="title"]').type('New Post')
    cy.get('textarea[name="body"]').type('Post body text')
    cy.get('button[type="submit"]').click()
    cy.wait('@createPost')
    cy.contains('New Post')
  })
})
```

## When to use

Cypress excels for end-to-end testing of web UIs and for component testing in React/Vue/Svelte projects. Its developer experience is the best in class for interactive, in-browser debugging. For cross-browser testing or non-browser test scenarios, Playwright supports Firefox and Safari and has a more powerful API for multi-page and multi-tab flows. For unit and integration tests, Jest or Vitest are more appropriate.
