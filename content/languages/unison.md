---
name: Unison
slug: unison
description: Functional language where code is content-addressed — functions are identified by hash, enabling distributed computing and fearless refactoring.
website: https://unison-lang.org
github: unisonweb/unison
year: 2019
paradigm: [functional, distributed, concurrent]
typing: static
compilation: compiled
tags: [distributed, functional, content-addressed, cloud, type-safe]
---

Unison stores code by the hash of its abstract syntax tree rather than by name — renaming a function never breaks anything. This content-addressed model enables Unison Cloud, where functions are deployed to distributed nodes by their hash. Its ability type system tracks effects (IO, exceptions, state) as a first-class feature.
