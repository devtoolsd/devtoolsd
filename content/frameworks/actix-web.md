---
name: Actix Web
slug: actix-web
language: rust
description: Powerful, high-performance Rust web framework — async-first, type-safe extractors, and consistently ranked among the world's fastest web servers.
logo: https://actix.rs/img/logo.png
website: https://actix.rs
github: actix/actix-web
year: 2017
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, rust, performance, async, api, rest, type-safe]
related_frameworks: [axum, rocket]
features:
  - "Consistently top-ranked in TechEmpower benchmarks"
  - "Type-safe extractors — `web::Json<T>`, `web::Path<T>`, `web::Query<T>`"
  - "Middleware system with request/response transformation"
  - "Built-in WebSocket support via actor system"
  - "App state sharing via `web::Data<T>` with `Arc` under the hood"
  - "Static file serving and streaming responses"
  - "Async handlers running on the Tokio runtime"
  - "Test utilities for in-process integration tests without binding a port"
install:
  cargo: "cargo add actix-web"
---

Actix Web consistently tops the TechEmpower benchmarks. Its extractor pattern — `web::Json<T>`, `web::Path<T>`, `web::Query<T>` — provides zero-overhead type-safe request parsing. Actix's actor system underpins WebSocket handling and stateful connections. It is the most widely deployed Rust web framework in production.

## Quick start

```toml
# Cargo.toml
[dependencies]
actix-web = "4"
serde = { version = "1", features = ["derive"] }
tokio = { version = "1", features = ["macros", "rt-multi-thread"] }
```

```rust
// src/main.rs
use actix_web::{get, post, web, App, HttpServer, Responder, HttpResponse};
use serde::{Deserialize, Serialize};

#[derive(Serialize, Deserialize, Clone)]
struct Post {
    id: u32,
    title: String,
    body: String,
}

#[get("/posts")]
async fn list_posts(data: web::Data<Vec<Post>>) -> impl Responder {
    HttpResponse::Ok().json(data.as_ref())
}

#[post("/posts")]
async fn create_post(post: web::Json<Post>) -> impl Responder {
    HttpResponse::Created().json(&post.into_inner())
}

#[actix_web::main]
async fn main() -> std::io::Result<()> {
    let posts: web::Data<Vec<Post>> = web::Data::new(vec![]);

    HttpServer::new(move || {
        App::new()
            .app_data(posts.clone())
            .service(list_posts)
            .service(create_post)
    })
    .bind("127.0.0.1:8080")?
    .run()
    .await
}
```

## When to use

Actix Web is the choice when raw throughput is critical — high-volume APIs, proxies, or services where latency matters. Rust's ownership model guarantees memory safety without GC pauses. For a more ergonomic Rust API with Tower middleware compatibility, Axum is worth comparing. Both are production-ready; the choice is mainly ecosystem preference (Tower vs Actix actors).
