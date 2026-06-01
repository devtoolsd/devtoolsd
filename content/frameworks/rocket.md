---
name: Rocket
slug: rocket
language: rust
description: Web framework for Rust focused on developer experience — type-checked routes, request guards, and zero-boilerplate handlers.
website: https://rocket.rs
github: rwf2/Rocket
year: 2016
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, rust, ergonomic, type-safe, api, rest, macros]
related_frameworks: [axum, actix-web]
features:
  - "Type-safe routing via procedural macros — `#[get(\"/posts/<id>\")]`"
  - "Request guards — implement `FromRequest` for custom auth and validation"
  - "Form and JSON data binding with validation"
  - "Built-in TLS support"
  - "State management with `State<T>` managed objects"
  - "Template rendering with Handlebars, Tera, or Minijinja"
  - "Fairing hooks for request/response middleware"
  - "Async support on Tokio runtime (Rocket 0.5+)"
install:
  cargo: "cargo add rocket"
---

Rocket uses procedural macros to validate routes, inputs, and guards at compile time — invalid routes simply don't compile. Its request guard trait provides a clean extension point for authentication, rate limiting, and validation. Rocket 0.5 added async support and is the most beginner-friendly Rust web framework for developers coming from Python or Ruby backgrounds.

## Quick start

```toml
# Cargo.toml
[dependencies]
rocket = { version = "0.5", features = ["json"] }
serde = { version = "1", features = ["derive"] }
```

```rust
// src/main.rs
#[macro_use] extern crate rocket;

use rocket::serde::{json::Json, Deserialize, Serialize};
use rocket::State;
use std::sync::Mutex;

#[derive(Debug, Serialize, Deserialize, Clone)]
#[serde(crate = "rocket::serde")]
struct Post {
    id: u32,
    title: String,
    body: String,
}

type Posts = Mutex<Vec<Post>>;

#[get("/posts")]
fn list_posts(posts: &State<Posts>) -> Json<Vec<Post>> {
    Json(posts.lock().unwrap().clone())
}

#[post("/posts", data = "<post>")]
fn create_post(post: Json<Post>, posts: &State<Posts>) -> Json<Post> {
    let mut store = posts.lock().unwrap();
    let mut p = post.into_inner();
    p.id = store.len() as u32 + 1;
    store.push(p.clone());
    Json(p)
}

#[get("/posts/<id>")]
fn get_post(id: u32, posts: &State<Posts>) -> Option<Json<Post>> {
    posts.lock().unwrap()
        .iter()
        .find(|p| p.id == id)
        .cloned()
        .map(Json)
}

#[launch]
fn rocket() -> _ {
    rocket::build()
        .manage(Posts::default())
        .mount("/api", routes![list_posts, create_post, get_post])
}
```

## When to use

Rocket is the most approachable Rust web framework for developers new to Rust — its macro-based API reads naturally and compile-time route checking catches errors early. Compared to Axum, Rocket has a more opinionated API with more built-in batteries. Axum has better Tower middleware compatibility and is the recommended choice for projects already in the Tokio ecosystem. Actix Web is faster at benchmarks. Choose Rocket for its ergonomics when learning Rust web development.
