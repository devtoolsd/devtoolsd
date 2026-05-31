---
name: Viper
slug: viper
language: go
description: Complete configuration solution for Go — reads from JSON, TOML, YAML, env vars, flags, and remote config stores.
website: https://github.com/spf13/viper
github: spf13/viper
year: 2014
pricing: free
open_source: true
license: MIT
library_type: utility
tags: [config, environment, yaml, toml, go, twelve-factor]
related_libraries: [cobra]
---

Viper resolves config from a priority chain — remote KV stores, environment variables, config files, default values — all with a single `viper.Get()` call. It watches config files for live reloading and integrates with Cobra so CLI flags and env vars automatically map to configuration keys.
