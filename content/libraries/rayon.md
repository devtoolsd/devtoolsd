---
name: Rayon
slug: rayon
language: rust
description: Data-parallelism library for Rust — parallel iterators that use all CPU cores with no unsafe code.
website: https://docs.rs/rayon
github: rayon-rs/rayon
year: 2015
pricing: free
open_source: true
license: MIT
library_type: utility
tags: [parallel, concurrency, performance, iterators, rust]
related_libraries: [tokio, serde]
---

Rayon turns `.iter()` into `.par_iter()` — that single change saturates all available CPU cores using a work-stealing thread pool. It handles nested parallelism automatically and composes with the standard iterator API. Ideal for CPU-bound batch processing in data pipelines and scientific computing.
