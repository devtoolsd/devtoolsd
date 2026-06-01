---
name: Prisma
slug: prisma
language: typescript
description: Next-generation TypeScript ORM — schema-first, auto-generated type-safe client, and Prisma Studio for data browsing.
logo: https://prismaio.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F06aaeab8-7584-4c11-b52b-b9be41e6cecc%2Fprisma-logo-3.png
website: https://prisma.io
github: prisma/prisma
year: 2016
pricing: freemium
open_source: true
license: Apache-2.0
tool_type: data
tags: [orm, database, typescript, postgresql, mysql, sqlite, schema, type-safe]
related_frameworks: [drizzle, sqlalchemy]
features:
  - "Schema-first — define your models in `schema.prisma`, generate a typed client"
  - "Auto-generated TypeScript types for every model and query"
  - "Prisma Migrate — SQL migrations from schema changes"
  - "Prisma Studio — visual data browser for your database"
  - "Prisma Accelerate — connection pooling and global query caching"
  - "Nested writes and transactions for complex operations"
  - "Supports PostgreSQL, MySQL, SQLite, MongoDB, SQL Server, CockroachDB"
  - "Raw SQL via `prisma.$queryRaw` when you need full control"
install:
  npm: "npm install prisma @prisma/client && npx prisma init"
  yarn: "yarn add prisma @prisma/client && yarn prisma init"
---

Prisma generates a fully type-safe database client from your schema file — every query is typed based on your exact data model. Prisma Migrate handles schema migrations, Prisma Studio provides a visual data browser, and Prisma Accelerate adds connection pooling and query caching. It is the most popular ORM in the TypeScript ecosystem, widely used with Next.js, Express, and NestJS.

## Quick start

```bash
npm install prisma @prisma/client
npx prisma init --datasource-provider postgresql
```

```prisma
// prisma/schema.prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model Post {
  id        Int      @id @default(autoincrement())
  title     String
  body      String
  published Boolean  @default(false)
  author    User     @relation(fields: [authorId], references: [id])
  authorId  Int
  createdAt DateTime @default(now())
}

model User {
  id    Int     @id @default(autoincrement())
  email String  @unique
  name  String?
  posts Post[]
}
```

```bash
npx prisma migrate dev --name init
npx prisma generate
```

```typescript
// src/db.ts
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()

// Fully typed — IDE knows the shape of every result
const posts = await prisma.post.findMany({
  where: { published: true },
  include: { author: true },
  orderBy: { createdAt: 'desc' },
})

const newPost = await prisma.post.create({
  data: {
    title: 'Hello Prisma',
    body: 'Type-safe database access.',
    author: { connect: { email: 'user@example.com' } },
  },
})
```

## When to use

Prisma is the default ORM choice for TypeScript Node.js projects. Its schema-first approach and generated types eliminate a whole class of runtime bugs. Prisma Studio makes database exploration easy during development. For teams that prefer writing SQL directly with TypeScript safety, Drizzle ORM is a lighter alternative. For Python projects, SQLAlchemy is the equivalent.
