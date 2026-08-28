---
name: Extenshi CLI
slug: extenshi-cli
website: https://docs.extenshi.io/developers/cli
description: Command-line pre-publish security scanner for browser extensions that also predicts Chrome Web Store review outcomes and publishes builds to Chrome, Firefox, and Edge.
long_description: |
  The Extenshi CLI runs against a packaged extension before you submit it to a store. It unpacks the build, scans the bundled code for security and privacy issues, and reports each finding with a severity, file, and line so it can be fixed while the release is still local. Alongside the scan it checks the build against Chrome Web Store review rules — permission justifications, Limited Use compliance, listing and manifest requirements — so submissions that would be rejected or delayed surface before upload, and a third command publishes the same build to the Chrome, Firefox, and Edge stores from your machine or from CI. Scanning uses an Extenshi API key; the publish and review-risk commands run entirely locally and need no account. It runs through npx, so there is nothing to install and every invocation resolves the current rule set.
tool_type: cli
pricing: freemium
open_source: false
logo: https://catalog.extenshi.io/logo.svg
docs_url: https://docs.extenshi.io/developers/cli
categories:
  - extensions
  - cli-tools
tags:
  - browser-extensions
  - security
  - manifest-v3
  - chrome-web-store
  - ci
platforms:
  - windows
  - macos
  - linux
languages:
  - typescript
features:
  - Pre-publish security and privacy scan of a packaged extension
  - Findings reported with severity, file, and line
  - Chrome Web Store review-risk check before you submit
  - Publish one build to Chrome, Firefox, and Edge
  - Runs in CI via GitHub Actions
install: |
  # requires Node 20+
  npx @extenshi/cli@latest scan ./dist/my-extension.zip
language: typescript
company: Extenshi
featured: false
---
