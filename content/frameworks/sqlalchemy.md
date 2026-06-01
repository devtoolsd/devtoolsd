---
name: SQLAlchemy
slug: sqlalchemy
language: python
description: Python SQL toolkit and ORM — both low-level SQL expression language and high-level ORM, the standard for Python database access.
website: https://sqlalchemy.org
github: sqlalchemy/sqlalchemy
year: 2006
pricing: free
open_source: true
license: MIT
tool_type: data
tags: [orm, database, sql, python, postgresql, mysql, sqlite, backend]
related_frameworks: [django, fastapi, flask]
features:
  - "ORM layer — map Python classes to tables with relationships and lazy loading"
  - "Core SQL expression language — write type-safe SQL without an ORM"
  - "Unit of Work pattern — batch changes and flush as a single transaction"
  - "Alembic for schema migrations (the standard SQLAlchemy migration tool)"
  - "Connection pooling with configurable pool size and recycling"
  - "Supports PostgreSQL, MySQL, SQLite, Oracle, SQL Server, and more"
  - "Async support via `asyncio` extension (SQLAlchemy 1.4+)"
  - "Works with FastAPI, Flask, and any Python web framework"
install:
  pip: "pip install sqlalchemy psycopg2-binary"
---

SQLAlchemy provides two distinct APIs — the Core SQL expression language for precise SQL control, and the ORM for mapping Python classes to tables. Its unit-of-work pattern, lazy loading, and connection pooling make it robust for complex applications. FastAPI and Flask both use SQLAlchemy as the recommended ORM. Alembic is its companion tool for database migrations.

## Quick start

```bash
pip install sqlalchemy psycopg2-binary alembic
```

```python
# models.py — SQLAlchemy ORM
from sqlalchemy import create_engine, Column, Integer, String, Text, DateTime, ForeignKey
from sqlalchemy.orm import DeclarativeBase, relationship, Session
from datetime import datetime

engine = create_engine("postgresql://user:pass@localhost/mydb", echo=True)

class Base(DeclarativeBase):
    pass

class User(Base):
    __tablename__ = "users"
    id = Column(Integer, primary_key=True)
    email = Column(String(255), unique=True, nullable=False)
    name = Column(String(100))
    posts = relationship("Post", back_populates="author", lazy="dynamic")

class Post(Base):
    __tablename__ = "posts"
    id = Column(Integer, primary_key=True)
    title = Column(String(200), nullable=False)
    body = Column(Text)
    created_at = Column(DateTime, default=datetime.utcnow)
    author_id = Column(Integer, ForeignKey("users.id"))
    author = relationship("User", back_populates="posts")

Base.metadata.create_all(engine)
```

```python
# queries.py
from sqlalchemy import select

with Session(engine) as session:
    # Create
    user = User(email="alice@example.com", name="Alice")
    session.add(user)
    session.commit()

    # Query with relationship
    posts = session.execute(
        select(Post)
        .join(Post.author)
        .where(User.name == "Alice")
        .order_by(Post.created_at.desc())
    ).scalars().all()

    # Update
    post = session.get(Post, 1)
    post.title = "Updated title"
    session.commit()
```

## When to use

SQLAlchemy is the standard for Python database access outside of Django. Its dual API (ORM + Core) lets you use high-level ORM for most work and drop to SQL expressions when needed. FastAPI's documentation recommends it, and it integrates with any Python web framework. For Django projects, the built-in ORM is tightly integrated and preferred. For async-first projects, SQLAlchemy async mode or SQLModel (built on SQLAlchemy) work well with FastAPI.
