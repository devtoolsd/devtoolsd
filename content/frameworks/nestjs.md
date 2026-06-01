---
name: NestJS
slug: nestjs
language: typescript
description: Progressive Node.js framework inspired by Angular — decorators, dependency injection, and modules for scalable server-side apps.
logo: https://upload.wikimedia.org/wikipedia/commons/a/a8/NestJS.svg
website: https://nestjs.com
github: nestjs/nest
year: 2017
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, nodejs, typescript, api, rest, graphql, microservices]
related_frameworks: [express, fastify, koa]
features:
  - "Module/Controller/Provider architecture for a consistent, scalable structure"
  - "Decorators and dependency injection inspired by Angular"
  - "Runs on Express or Fastify — swap the HTTP adapter without rewriting logic"
  - "Built-in support for REST, GraphQL, WebSockets, and microservice transports"
  - "Guards, interceptors, pipes, and filters for cross-cutting concerns"
  - "First-class TypeScript — strict mode by default"
  - "CLI for scaffolding modules, controllers, services, and more"
  - "Extensive documentation and enterprise backing (Trilon)"
install:
  npm: "npm i -g @nestjs/cli && nest new my-app"
  npx: "npx @nestjs/cli new my-app"
---

NestJS brings Angular's architecture to backend development — modules, controllers, providers, and guards give large teams a consistent structure across a large codebase. It can run on Express or Fastify underneath and supports REST, GraphQL, WebSockets, and microservice transports (Kafka, RabbitMQ, gRPC) out of the box. Its strong opinions about structure make it especially valuable when multiple engineers need to work on the same codebase without stepping on each other.

## Quick start

```bash
npm i -g @nestjs/cli
nest new my-app
cd my-app
npm run start:dev
```

```typescript
// src/posts/post.entity.ts
export class Post {
  id: number
  title: string
  body: string
}

// src/posts/posts.service.ts
import { Injectable, NotFoundException } from '@nestjs/common'
import { Post } from './post.entity'

@Injectable()
export class PostsService {
  private posts: Post[] = []

  findAll(): Post[] { return this.posts }

  findOne(id: number): Post {
    const post = this.posts.find(p => p.id === id)
    if (!post) throw new NotFoundException(`Post #${id} not found`)
    return post
  }

  create(data: Omit<Post, 'id'>): Post {
    const post = { id: this.posts.length + 1, ...data }
    this.posts.push(post)
    return post
  }
}

// src/posts/posts.controller.ts
import { Controller, Get, Post, Body, Param, ParseIntPipe } from '@nestjs/common'
import { PostsService } from './posts.service'

@Controller('posts')
export class PostsController {
  constructor(private readonly postsService: PostsService) {}

  @Get()
  findAll() { return this.postsService.findAll() }

  @Get(':id')
  findOne(@Param('id', ParseIntPipe) id: number) {
    return this.postsService.findOne(id)
  }

  @Post()
  create(@Body() body: { title: string; body: string }) {
    return this.postsService.create(body)
  }
}
```

## When to use

NestJS is ideal for TypeScript teams building large Node.js backends that need a consistent, opinionated architecture. Its module system and dependency injection shine when multiple developers need clear ownership boundaries. For smaller APIs or teams that prefer flexibility, Express or Fastify without NestJS is simpler. If your frontend is already Angular, NestJS's shared patterns make the stack feel unified.
