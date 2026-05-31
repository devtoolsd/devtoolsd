---
name: Click
slug: click
language: python
description: Composable command-line interface toolkit for Python — decorators turn functions into commands with options, arguments, and help text.
website: https://click.palletsprojects.com
github: pallets/click
year: 2014
pricing: free
open_source: true
license: BSD-3-Clause
library_type: cli
tags: [cli, argparse, commands, python, terminal, devtools]
frameworks: [flask]
related_libraries: [rich]
---

Click uses a decorator-based API — `@click.command()`, `@click.option()`, and `@click.argument()` transform any Python function into a fully featured CLI with automatic `--help` generation, type coercion, and shell completion. Flask uses Click for its own CLI; FastAPI and many ML tools build CLIs on top of it.
