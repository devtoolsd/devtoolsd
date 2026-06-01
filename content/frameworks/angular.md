---
name: Angular
slug: angular
language: typescript
description: Full-featured TypeScript framework from Google — opinionated, batteries-included, built for large-scale enterprise SPAs.
logo: https://upload.wikimedia.org/wikipedia/commons/c/cf/Angular_full_color_logo.svg
website: https://angular.dev
github: angular/angular
year: 2016
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [frontend, spa, typescript, enterprise, google, components]
related_frameworks: [react, vue, svelte]
features:
  - "Built-in dependency injection — services are injected, not imported"
  - "TypeScript-first — strict typing enforced across the entire framework"
  - "Angular CLI for generating components, services, guards, and pipes"
  - "RxJS-based reactivity — Observables for async data streams"
  - "Reactive Forms and Template-Driven Forms with validation"
  - "Angular Router with lazy loading, guards, and resolvers"
  - "HttpClient with interceptors for auth headers and error handling"
  - "Signals API (v17+) for fine-grained reactivity without RxJS"
install:
  npm: "npm install -g @angular/cli && ng new my-app"
  npx: "npx @angular/cli new my-app"
---

Angular provides a complete, opinionated solution — dependency injection, reactive forms, routing, and HTTP all built in and maintained by Google. Its strict TypeScript integration and CLI-driven development make it the dominant choice for large enterprise teams building complex SPAs. Unlike React and Vue, Angular is a full framework — you don't assemble it from libraries; everything follows Angular's conventions. Angular 17+ introduces Signals for simpler reactivity and standalone components that no longer require NgModules.

## Quick start

```bash
npm install -g @angular/cli
ng new my-app --routing --style=scss
cd my-app
ng serve
```

```typescript
// Generate a component and service
ng generate component posts
ng generate service posts/post
```

```typescript
// src/app/posts/post.service.ts
import { Injectable } from '@angular/core'
import { HttpClient } from '@angular/common/http'
import { Observable } from 'rxjs'

export interface Post { id: number; title: string; body: string }

@Injectable({ providedIn: 'root' })
export class PostService {
  constructor(private http: HttpClient) {}

  getPosts(): Observable<Post[]> {
    return this.http.get<Post[]>('/api/posts')
  }
}

// src/app/posts/posts.component.ts
import { Component, OnInit } from '@angular/core'
import { PostService, Post } from './post.service'

@Component({
  selector: 'app-posts',
  template: `
    <ul>
      <li *ngFor="let post of posts">{{ post.title }}</li>
    </ul>
  `,
})
export class PostsComponent implements OnInit {
  posts: Post[] = []

  constructor(private postService: PostService) {}

  ngOnInit() {
    this.postService.getPosts().subscribe(posts => this.posts = posts)
  }
}
```

## When to use

Angular is the right choice for large enterprise SPAs where a highly opinionated, consistent structure is more valuable than flexibility. Its strong TypeScript enforcement, dependency injection, and CLI tooling scale well across large teams. For smaller apps or teams that prefer a lighter touch, React or Vue have lower overhead. If you're already using Angular on a project, staying on it and upgrading is almost always better than migrating.
