---
name: Pony
slug: pony
description: Actor-based object-oriented language with a capability-security type system — data-race free and deadlock free by design.
website: https://ponylang.io
github: ponylang/ponyc
year: 2014
paradigm: [oop, concurrent, actor-model]
typing: static
compilation: compiled
tags: [concurrent, actor-model, type-safe, systems, performance]
---

Pony's reference capability system encodes aliasing and mutability at the type level, making data races and deadlocks impossible by construction — not just unlikely, but unrepresentable. Its actor model uses work-stealing for efficient concurrency without locks. Pony compiles to native code via LLVM and is used in research into safe high-performance concurrent systems.
