---
name: Tokio
slug: tokio
language: rust
description: Async runtime for Rust — event-driven, non-blocking I/O, task scheduling, and networking primitives.
website: https://tokio.rs
github: tokio-rs/tokio
year: 2016
pricing: free
open_source: true
license: MIT
library_type: async
tags: [async, runtime, networking, io, rust, concurrency]
frameworks: [axum, actix-web, rocket]
related_libraries: [serde, rayon]
---

Tokio is the de facto async runtime for Rust — virtually every async Rust project targets its executor. It provides a multi-threaded scheduler, async TCP/UDP sockets, timers, and a channel ecosystem (`mpsc`, `oneshot`, `broadcast`). Axum, Tonic, and Reqwest all run on Tokio.
