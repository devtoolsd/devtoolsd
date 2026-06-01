---
name: Vert.x
slug: vert-x
language: java
description: Reactive toolkit for building event-driven applications on the JVM — polyglot, non-blocking, and massively scalable.
logo: https://upload.wikimedia.org/wikipedia/commons/c/c4/Vert.x_Logo.svg
website: https://vertx.io
github: eclipse-vertx/vert.x
year: 2011
pricing: free
open_source: true
license: Apache-2.0
tool_type: web
tags: [backend, java, reactive, event-driven, non-blocking, polyglot, microservices]
related_frameworks: [spring-boot, quarkus, micronaut]
features:
  - "Non-blocking event loop — single thread handles thousands of concurrent connections"
  - "Polyglot — write Verticles in Java, Kotlin, Groovy, JavaScript, Scala, or Ruby"
  - "Event bus — lightweight messaging across Verticles and cluster nodes"
  - "Reactive streams — backpressure-aware I/O via RxJava or Mutiny"
  - "Vert.x Web — routing, body parsing, static files, sessions, and auth handlers"
  - "Vert.x SQL Client — reactive, non-blocking drivers for PostgreSQL, MySQL, MSSQL"
  - "Clustering via Hazelcast or Infinispan — distributed event bus across JVM nodes"
  - "Native image support with GraalVM for sub-10ms startup times"
install:
  gradle: "implementation 'io.vertx:vertx-web:4.5.10'"
  maven: "<artifactId>vertx-web</artifactId><version>4.5.10</version>"
---

Vert.x is built on a non-blocking event loop model — a single thread handles thousands of concurrent connections without thread-per-request overhead. It is polyglot by design: Verticles (the unit of deployment) can be written in Java, Kotlin, Groovy, JavaScript, Scala, or Ruby and communicate over a shared event bus. Unlike Spring Boot's thread-per-request model, Vert.x never blocks the event loop, making it one of the highest-throughput JVM frameworks. Used at Red Hat, Hulu, and in high-frequency financial systems where latency and memory efficiency are critical.

## Quick start

```kotlin
// build.gradle.kts
dependencies {
    implementation("io.vertx:vertx-web:4.5.10")
    implementation("io.vertx:vertx-lang-kotlin:4.5.10")
    implementation("io.vertx:vertx-lang-kotlin-coroutines:4.5.10")
}
```

```kotlin
// src/main/kotlin/MainVerticle.kt
import io.vertx.ext.web.Router
import io.vertx.kotlin.coroutines.CoroutineVerticle
import io.vertx.kotlin.coroutines.coAwait

class MainVerticle : CoroutineVerticle() {
    override suspend fun start() {
        val router = Router.router(vertx)

        router.get("/posts").handler { ctx ->
            ctx.json(listOf(mapOf("id" to 1, "title" to "Hello Vert.x")))
        }

        router.post("/posts").handler { ctx ->
            val body = ctx.body().asJsonObject()
            ctx.response().setStatusCode(201)
            ctx.json(mapOf("id" to 2, "title" to body.getString("title")))
        }

        vertx.createHttpServer()
            .requestHandler(router)
            .listen(8080)
            .coAwait()

        println("Server listening on port 8080")
    }
}
```

```kotlin
// Main.kt
import io.vertx.core.Vertx

fun main() {
    Vertx.vertx().deployVerticle(MainVerticle())
}
```

## When to use

Vert.x is the right choice for JVM services that need maximum throughput and minimum latency — websocket servers, real-time APIs, and event-driven microservices where thread-per-request overhead is unacceptable. Its polyglot event bus makes it a strong fit for teams that mix JVM languages. For teams that prefer convention over configuration and a larger ecosystem of starters, Spring Boot or Quarkus are easier to onboard. For Kubernetes-native JVM microservices, Quarkus and Micronaut offer more integrated cloud tooling, while Vert.x shines when raw reactive performance is the priority.
