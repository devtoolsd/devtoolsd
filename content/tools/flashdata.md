---
name: FlashData
slug: flashdata
website: https://flashdata.dev/?utm_source=devtoolsdirectory
description: Paid APIs for YouTube media downloads to your storage, YouTube metadata and existing captions, and structured Google search results.
tool_type: api
pricing: paid
open_source: false
logo: /img/logos/tools/flashdata.png
docs_url: https://flashdata.dev/docs?utm_source=devtoolsdirectory
tags:
  - api
  - youtube
  - search
  - mcp
features:
  - YouTube videos, audio and clips delivered to your own cloud storage
  - YouTube metadata, channel information and existing captions as JSON
  - Google web, news, image, shopping, video and place search results
  - REST APIs and MCP access with one account and API key
company: FlashData
featured: false
---

FlashData provides three hosted API products for applications and AI assistants.

## YouTube Download

The Download API delivers videos, audio and selected clips to your own Amazon S3,
Google Cloud Storage, Azure Blob or S3-compatible storage. It supports asynchronous
jobs, batches and file-based Bulk collections. You need storage write access and
the necessary usage rights. Billing is based on delivered media bytes;
storage-provider charges may apply separately.

## YouTube Data

The Data API returns search results, video metadata, existing transcripts and
captions, channel details, suggestions and license-label information as JSON.
Standard Search supports up to 20 results; Extended Search supports up to 700,
subject to availability and a separate rate. Bulk handles metadata, existing
captions and license checks from video-ID files. It does not transcribe audio or
translate captions. A license label does not establish reuse or training rights.

## Google Search

The Search API returns web, news, image, shopping, video and place results as
structured JSON, with country, language and location controls. Realtime,
asynchronous and batch requests support research and search applications. Results
contain links, snippets and available fields, not full linked-page content. Each
query is billed separately.

## Pricing and trial

Usage is paid. Eligible new accounts receive one shared, one-time trial Credits
balance after email verification and account setup, with no credit card required.
There is no recurring free tier or separate trial allowance per API. Pay-as-you-go
does not require a monthly subscription; optional subscriptions are also available.

The MCP client is MIT-licensed, but this listing describes the hosted API service,
which is not open source. The client license does not make hosted API usage free.
Consult the linked official documentation and current pricing before production use.
