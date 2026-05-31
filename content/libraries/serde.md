---
name: Serde
slug: serde
language: rust
description: Serialization and deserialization framework for Rust — derive macros generate blazing-fast JSON, TOML, YAML, and more.
website: https://serde.rs
github: serde-rs/serde
year: 2014
pricing: free
open_source: true
license: MIT
library_type: serialization
tags: [serialization, json, toml, yaml, rust, macros]
frameworks: [axum, actix-web, rocket]
related_libraries: [tokio]
---

Serde's `#[derive(Serialize, Deserialize)]` macros make struct-to-JSON round-trips trivial with zero runtime overhead. The trait system allows any format (JSON via `serde_json`, TOML via `toml`, YAML via `serde_yaml`, MessagePack, bincode) to plug in without changing application code.
