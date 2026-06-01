---
name: pytest
slug: pytest
language: python
description: The standard Python testing framework — simple assert statements, powerful fixtures, and a vast plugin ecosystem.
website: https://pytest.org
github: pytest-dev/pytest
year: 2004
pricing: free
open_source: true
license: MIT
tool_type: testing
tags: [testing, python, unit-testing, fixtures, plugins, parametrize]
related_frameworks: [unittest]
features:
  - "Plain `assert` statements — no verbose `self.assertEqual()` required"
  - "Automatic test discovery in `test_*.py` files"
  - "Fixtures with dependency injection and scope (function/class/session)"
  - "`@pytest.mark.parametrize` for data-driven tests"
  - "1000+ plugins: pytest-cov, pytest-xdist, pytest-django, pytest-asyncio"
  - "Detailed failure output with diffs and local variable inspection"
  - "Markers for grouping and skipping tests"
  - "Compatible with `unittest.TestCase` for gradual migration"
install:
  pip: "pip install pytest"
---

pytest replaces Python's verbose `unittest` with plain assert statements, automatic test discovery, and a fixture system that handles setup/teardown with dependency injection. Over 1,000 plugins extend it with coverage, parallel execution, Django integration, snapshot testing, and more. It is the de facto standard for Python testing across all domains — web, CLI, data science, and libraries.

## Quick start

```bash
pip install pytest pytest-cov
```

```python
# src/math_utils.py
def add(a: int, b: int) -> int:
    return a + b

def divide(a: float, b: float) -> float:
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
```

```python
# tests/test_math_utils.py
import pytest
from src.math_utils import add, divide

def test_add_returns_sum():
    assert add(2, 3) == 5

def test_add_handles_negatives():
    assert add(-1, 1) == 0

@pytest.mark.parametrize("a,b,expected", [
    (1, 2, 3),
    (0, 0, 0),
    (-5, 5, 0),
])
def test_add_parametrised(a, b, expected):
    assert add(a, b) == expected

def test_divide_raises_on_zero():
    with pytest.raises(ValueError, match="Cannot divide by zero"):
        divide(10, 0)
```

```python
# Fixtures example
import pytest

@pytest.fixture
def db_connection():
    conn = create_test_db()
    yield conn          # test runs here
    conn.rollback()     # teardown

def test_save_post(db_connection):
    post = Post(title="Hello", body="World")
    db_connection.save(post)
    assert db_connection.find(Post, post.id) is not None
```

```bash
pytest                    # run all tests
pytest -v                 # verbose output
pytest --cov=src          # with coverage
pytest -k "add"           # only tests matching 'add'
pytest -x                 # stop on first failure
```

## When to use

pytest is the standard Python testing framework and should be the default for any Python project. Its fixture system is the most powerful and ergonomic of any language's testing framework. Use pytest-asyncio for testing async code, pytest-django for Django, pytest-cov for coverage, and pytest-xdist for parallel test execution. Migrating from `unittest` is straightforward — pytest runs `unittest.TestCase` tests natively.
