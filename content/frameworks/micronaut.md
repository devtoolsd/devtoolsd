---
name: Micronaut
slug: micronaut
language: java
description: JVM microservices framework with compile-time dependency injection — no reflection, fast startup, and low memory.
logo: https://upload.wikimedia.org/wikipedia/commons/3/3a/Micronaut_Framework_Logo.png
website: https://micronaut.io
github: micronaut-projects/micronaut-core
year: 2018
pricing: free
open_source: true
license: Apache-2.0
tool_type: web
tags: [backend, java, microservices, cloud-native, kotlin, groovy, fast-startup]
related_frameworks: [spring-boot, quarkus, vert-x]
features:
  - "Compile-time DI — no runtime reflection, fast startup and low memory"
  - "GraalVM native image support out of the box"
  - "Cloud-native — Kubernetes health checks, distributed config, service discovery"
  - "Micronaut Data — type-safe JPA and SQL queries generated at compile time"
  - "HTTP client with Kotlin coroutines and RxJava support"
  - "Supports Java, Kotlin, and Groovy in the same project"
  - "Serverless support for AWS Lambda, Azure Functions, GCP"
  - "Micronaut Test with embedded server for fast integration tests"
install:
  sdkman: "sdk install micronaut && mn create-app my-app"
  homebrew: "brew install micronaut && mn create-app my-app"
---

Micronaut processes annotations at compile time rather than runtime reflection, eliminating Spring's slow startup and high memory usage. It supports Java, Kotlin, and Groovy and provides first-class support for GraalVM native images, serverless functions, and service discovery. Its compile-time approach means startup in milliseconds — ideal for Lambda functions and containerised microservices.

## Quick start

```bash
sdk install micronaut
mn create-app com.example.my-app --build=gradle --lang=kotlin
cd my-app
./gradlew run
```

```kotlin
// src/main/kotlin/com/example/PostController.kt
import io.micronaut.http.annotation.*
import io.micronaut.http.HttpStatus
import jakarta.inject.Singleton

data class Post(val id: Int, val title: String, val body: String)

@Singleton
class PostService {
    private val posts = mutableListOf<Post>()

    fun findAll(): List<Post> = posts

    fun save(post: Post): Post {
        val saved = post.copy(id = posts.size + 1)
        posts.add(saved)
        return saved
    }
}

@Controller("/posts")
class PostController(private val service: PostService) {

    @Get
    fun list() = service.findAll()

    @Post
    @Status(HttpStatus.CREATED)
    fun create(@Body post: Post) = service.save(post)
}
```

## When to use

Micronaut is ideal for Java/Kotlin microservices that need fast startup, low memory footprint, and cloud-native features. It's particularly strong for serverless (AWS Lambda) and Kubernetes deployments where container startup time matters. Quarkus is its closest competitor with similar compile-time philosophy. For teams with deep Spring Boot expertise, the migration cost to Micronaut may not be worthwhile unless startup time is a bottleneck.
