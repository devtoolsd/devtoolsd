---
name: Vale
slug: vale
description: Fast, safe systems language using generational references instead of a borrow checker — aims for Rust-level safety with simpler ergonomics.
website: https://vale.dev
github: ValeLang/Vale
year: 2020
paradigm: [imperative, systems, oop]
typing: static
compilation: compiled
tags: [systems, memory-safety, performance, native, experimental]
---

Vale achieves memory safety through generational references — every allocation has a generation number, and pointer reads check the generation at runtime, catching use-after-free without requiring a borrow checker. This trades a small runtime overhead for dramatically simpler code compared to Rust. Vale is pre-1.0 and targeting game development and systems programming as primary domains.
