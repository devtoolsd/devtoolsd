---
name: Tauri
slug: tauri
language: rust
description: Build tiny, fast desktop apps with a Rust core and any web frontend — 10x smaller bundles than Electron with lower memory usage.
logo: https://tauri.app/meta/tauri_logo_light.svg
website: https://tauri.app
github: tauri-apps/tauri
year: 2020
pricing: free
open_source: true
license: MIT
tool_type: desktop
tags: [desktop, cross-platform, rust, webview, performance, security, lightweight]
related_frameworks: [electron]
features:
  - "Uses the OS WebView — no bundled Chromium, app sizes under 10MB"
  - "Rust backend — system APIs, file access, and native OS integration"
  - "Works with any web frontend — React, Vue, Svelte, Solid, vanilla JS"
  - "Tauri 2 — mobile support for iOS and Android"
  - "IPC via Tauri commands — call Rust functions from JavaScript"
  - "System tray, notifications, file dialogs, shell commands"
  - "App security model — explicit permission list for each Tauri API"
  - "Auto-updater via Tauri's built-in update mechanism"
install:
  npm: "npm create tauri-app@latest my-app"
  cargo: "cargo install tauri-cli && cargo tauri init"
---

Tauri uses the OS's built-in WebView (WebKit on macOS/Linux, WebView2 on Windows) instead of bundling Chromium, resulting in app sizes under 10MB vs. Electron's 100MB+. The Rust backend handles system integration securely with an explicit permission model. Tauri 2 added mobile support for iOS and Android from the same codebase, making it the most versatile cross-platform framework for web developers.

## Quick start

```bash
# Prerequisites: Rust, Node.js
npm create tauri-app@latest my-app
# Select: frontend framework (React/Vue/Svelte/etc)
cd my-app && npm install
npm run tauri dev
```

```rust
// src-tauri/src/main.rs
use tauri::Manager;

#[tauri::command]
fn read_file(path: String) -> Result<String, String> {
    std::fs::read_to_string(&path)
        .map_err(|e| e.to_string())
}

#[tauri::command]
fn greet(name: &str) -> String {
    format!("Hello, {}!", name)
}

fn main() {
    tauri::Builder::default()
        .invoke_handler(tauri::generate_handler![greet, read_file])
        .run(tauri::generate_context!())
        .expect("error while running tauri application");
}
```

```typescript
// Frontend — call Rust functions from JavaScript
import { invoke } from '@tauri-apps/api/core'

const greeting = await invoke<string>('greet', { name: 'World' })
console.log(greeting)  // "Hello, World!"

const contents = await invoke<string>('read_file', { path: '/etc/hosts' })
```

## When to use

Tauri is the right choice when you want a desktop app with a web frontend but can't accept Electron's bundle size or memory overhead. Its Rust backend provides better security and performance for system-level operations. For teams that don't know Rust but need simple OS integration, Electron's JavaScript backend is simpler. Tauri 2's mobile support makes it the most complete web-based cross-platform solution for developers who can write Rust. If you're already building with React, Vue, or Svelte, Tauri slots in without changing your frontend stack.
