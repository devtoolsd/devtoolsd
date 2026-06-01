---
name: Mocha
slug: mocha
language: javascript
description: Flexible JavaScript test runner — browser and Node.js support, unopinionated about assertions and mocking.
website: https://mochajs.org
github: mochajs/mocha
year: 2011
pricing: free
open_source: true
license: MIT
tool_type: testing
tags: [testing, javascript, nodejs, bdd, tdd, browser, flexible]
related_frameworks: [jest, vitest, chai]
features:
  - "BDD and TDD interfaces — `describe()`/`it()` or `suite()`/`test()`"
  - "Unopinionated — pair with Chai, assert, or any assertion library"
  - "Async support — Promises, async/await, and callbacks"
  - "Flexible reporter system — spec, dot, tap, nyan, json, junit"
  - "Browser test runner support"
  - "Retry flaky tests with `--retries`"
  - "Parallel test execution with `--parallel` flag"
  - "Root hooks for global setup/teardown"
install:
  npm: "npm install --save-dev mocha chai"
  yarn: "yarn add -D mocha chai"
---

Mocha is a flexible test runner that doesn't include assertions or mocking — you pair it with Chai for assertions and Sinon for spies. This flexibility made it the dominant Node.js testing framework before Jest's rise. It remains widely used in projects that prefer modular testing toolchains, in browser environments, and in older codebases.

## Quick start

```bash
npm install --save-dev mocha chai
```

```javascript
// test/math.test.js
const { expect } = require('chai')
const { add, divide } = require('../src/math')

describe('add()', () => {
  it('returns the sum of two numbers', () => {
    expect(add(2, 3)).to.equal(5)
  })

  it('handles negative numbers', () => {
    expect(add(-1, 1)).to.equal(0)
  })
})

describe('divide()', () => {
  it('divides two numbers', () => {
    expect(divide(10, 2)).to.equal(5)
  })

  it('throws on division by zero', () => {
    expect(() => divide(5, 0)).to.throw('Division by zero')
  })
})

// Async test
describe('fetchUser()', () => {
  it('returns a user object', async () => {
    const user = await fetchUser(1)
    expect(user).to.have.property('name')
    expect(user.id).to.equal(1)
  })
})
```

```json
// package.json
{
  "scripts": {
    "test": "mocha 'test/**/*.test.js'",
    "test:watch": "mocha --watch 'test/**/*.test.js'"
  }
}
```

## When to use

Mocha is a reasonable choice when you want full control over your assertion library (Chai) and mocking library (Sinon) independently, or when you're running tests in the browser. For new JavaScript/TypeScript projects, Jest or Vitest offer a more integrated experience with built-in mocking, snapshots, and better TypeScript support. Mocha remains relevant for maintaining existing test suites and projects that need its flexible reporter ecosystem.
