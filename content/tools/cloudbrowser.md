---
name: Cloudbrowser
slug: cloudbrowser
website: https://cloudbrowser.tv/
description: Persistent, isolated Chrome cloud browsers for AI agents with CDP automation and permission-controlled Live View.
tool_type: platform
open_source: false
docs_url: https://cloudbrowser.tv/docs
categories:
  - devops
  - testing
tags:
  - cloud-browser
  - browser-automation
  - ai-agent-infrastructure
  - cdp
featured: false
---

Cloudbrowser provides isolated Chrome browser profiles for agent-driven web tasks. It exposes CDP connections for automation and permission-controlled Live View for observing or controlling a browser. Browser profiles can retain cookies and local storage across tasks. Browsers can be paused and resumed, and a paused browser can be forked into an independent browser.

The service is currently an **invitation-only private preview**. Runtime access requires an invited account or workspace API key. Resume restarts Chrome; it does not preserve process memory, and website sessions can expire. Fork requires a paused source browser. The Go CLI is a proposed design and has not been released.

The published Free plan includes one browser-hour per UTC month and one concurrent browser. Basic and Pro are pricing previews; billing is not enabled, so they are not currently purchasable subscriptions.

Sources: [documentation](https://cloudbrowser.tv/docs), [browser lifecycle](https://cloudbrowser.tv/docs/browsers), [connections](https://cloudbrowser.tv/docs/connections), [security](https://cloudbrowser.tv/docs/security), and [pricing](https://cloudbrowser.tv/pricing), reviewed 1 November 2026. Protocol examples in the documentation do not establish independently tested end-to-end integrations.
