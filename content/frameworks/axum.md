---
name: Axum
slug: axum
language: rust
description: Ergonomic Rust web framework from the Tokio team — macro-free routing, extractors, and seamless Tower middleware compatibility.
website: https://docs.rs/axum
github: tokio-rs/axum
year: 2021
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, rust, async, tokio, tower, api, rest, ergonomic]
related_frameworks: [actix-web, rocket]
features:
  - "Macro-free routing — no derive macros or codegen, just Rust functions"
  - "Full Tower middleware compatibility — tower-http for logging, CORS, auth"
  - "Type-safe extractors via `FromRequest` trait — extend with your own"
  - "State sharing via `State<T>` extractor — thread-safe and clone-friendly"
  - "WebSocket upgrade handling"
  - "SSE (Server-Sent Events) support"
  - "Nesting and merging routers for modular applications"
  - "Native async/await on Tokio runtime"
install:
  cargo: "cargo add axum tokio --features tokio/full"
---

Axum is built on Tokio and the Tower ecosystem — any Tower middleware (rate limiting, tracing, auth) works out of the box. Its macro-free routing and type-safe extractors provide an ergonomic API without code generation. Axum has rapidly become the preferred Rust web framework for new projects, especially those already using Tokio for async I/O.

## Quick start

```toml
# Cargo.toml
[dependencies]
axum = "0.7"
tokio = { version = "1", features = ["full"] }
serde = { version = "1", features = ["derive"] }
serde_json = "1"
```

```rust
// src/main.rs
use axum::{
    extract::{Path, State},
    http::StatusCode,
    routing::{get, post},
    Json, Router,
};
use serde::{Deserialize, Serialize};
use std::sync::{Arc, Mutex};

#[derive(Serialize, Deserialize, Clone)]
struct Post { id: u32, title: String, body: String }

type AppState = Arc<Mutex<Vec<Post>>>;

#[tokio::main]
async fn main() {
    let state: AppState = Arc::new(Mutex::new(vec![]));

    let app = Router::new()
        .route("/posts", get(list_posts).post(create_post))
        .route("/posts/:id", get(get_post))
        .with_state(state);

    let listener = tokio::net::TcpListener::bind("0.0.0.0:3000").await.unwrap();
    axum::serve(listener, app).await.unwrap();
}

async fn list_posts(State(state): State<AppState>) -> Json<Vec<Post>> {
    Json(state.lock().unwrap().clone())
}

async fn get_post(
    Path(id): Path<u32>,
    State(state): State<AppState>,
) -> Result<Json<Post>, StatusCode> {
    state.lock().unwrap()
        .iter().find(|p| p.id == id)
        .cloned().map(Json)
        .ok_or(StatusCode::NOT_FOUND)
}

async fn create_post(
    State(state): State<AppState>,
    Json(mut post): Json<Post>,
) -> (StatusCode, Json<Post>) {
    let mut posts = state.lock().unwrap();
    post.id = posts.len() as u32 + 1;
    posts.push(post.clone());
    (StatusCode::CREATED, Json(post))
}
```

## When to use

Axum is the recommended starting point for new Rust web services. Its seamless Tower middleware integration means you get production-ready observability (tracing), security (headers), and rate limiting without leaving the ecosystem. Compared to Actix Web, Axum is slightly less performant at extreme benchmarks but has a more ergonomic API and no dependency on the Actix actor system. For Tokio-native projects, Axum is the natural fit.
