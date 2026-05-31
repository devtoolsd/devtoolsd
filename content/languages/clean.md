---
name: Clean
slug: clean
description: Purely functional language from the Netherlands with uniqueness types for safe in-place mutation without monads.
website: https://clean-lang.org
year: 1987
paradigm: [functional, lazy]
typing: static
compilation: compiled
tags: [functional, type-theory, uniqueness-types, academic, haskell-like]
---

Clean is a lazily-evaluated, purely functional language similar to Haskell, but with uniqueness types instead of monads for handling state and I/O. Uniqueness types allow safe in-place mutation of values when it can be proved only one reference exists. Clean compiles to highly efficient native code and influenced the linear and affine type systems in Rust and other languages.
