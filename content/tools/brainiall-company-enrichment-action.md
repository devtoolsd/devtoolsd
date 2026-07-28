---
name: Brainiall Company Enrichment Action
slug: brainiall-company-enrichment-action
website: https://github.com/fasuizu-br/brainiall-company-enrichment-action
description: Source-backed company website metadata for one domain in GitHub Actions or n8n, with bounded Apify usage.
long_description: |
  Enriches one user-supplied company domain with a validated website-metadata
  candidate from the Brainiall Company Enrichment Actor on Apify. Results are
  website-derived hints for human review, not authoritative registry, credit,
  email, or compliance data. The included GitHub Action and n8n workflow cap a
  request at one result and US$0.02.
tool_type: api
pricing: freemium
open_source: true
license: MIT
github: fasuizu-br/brainiall-company-enrichment-action
docs_url: https://github.com/fasuizu-br/brainiall-company-enrichment-action#readme
tags:
  - company-data
  - github-actions
  - n8n
  - apify
  - automation
platforms:
  - linux
features:
  - Accepts exactly one bare company domain
  - Returns one source-backed website-metadata candidate
  - Caps each request at one result and US$0.02
  - Keeps the caller's Apify token in secret storage
company: BRAINIALL
featured: false
---

Use only domains and data you are entitled to process. Review every candidate
before using it in a CRM, procurement workflow, or business decision.
