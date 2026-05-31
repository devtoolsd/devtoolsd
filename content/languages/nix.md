---
name: Nix
slug: nix
description: Purely functional configuration language for the Nix package manager — enables reproducible builds and declarative system configuration.
website: https://nixos.org/manual/nix/stable/language/
github: NixOS/nix
year: 2003
paradigm: [functional, declarative, configuration]
typing: dynamic
compilation: interpreted
tags: [devops, configuration, reproducible, package-management, nixos]
---

The Nix language is a lazily-evaluated, purely functional expression language used to describe packages, their dependencies, and system configurations. Everything in Nix is an expression that evaluates to a derivation — a precise, reproducible build specification. NixOS uses it to describe an entire Linux system, enabling atomic upgrades and rollbacks.
