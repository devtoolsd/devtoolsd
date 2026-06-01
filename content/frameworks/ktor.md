---
name: Ktor
slug: ktor
language: kotlin
description: Async Kotlin framework from JetBrains — coroutine-native, multiplatform, for both server-side and client HTTP.
logo: https://upload.wikimedia.org/wikipedia/commons/0/0d/Ktor_logo.svg
website: https://ktor.io
github: ktorio/ktor
year: 2017
pricing: free
open_source: true
license: Apache-2.0
tool_type: web
tags: [backend, kotlin, async, coroutines, api, rest, jetbrains, multiplatform]
related_frameworks: [spring-boot, micronaut]
features:
  - "Coroutine-native — every handler is a `suspend` function"
  - "Plugin-based architecture — install only what you need"
  - "Type-safe routing with Kotlin DSL"
  - "Content negotiation — JSON, XML, CBOR out of the box"
  - "Ktor Client — multiplatform HTTP client for JVM, Android, iOS, JS"
  - "WebSocket and SSE support"
  - "Authentication plugins — JWT, OAuth, Basic, Session"
  - "GraalVM native image support for fast startup"
install:
  gradle: "implementation(\"io.ktor:ktor-server-core-jvm\") // in build.gradle.kts"
---

Ktor is built around Kotlin coroutines — every handler is a suspend function, making async code read like synchronous code. Its plugin-based architecture (routing, auth, serialisation, WebSockets) keeps the core minimal and composable. Ktor Multiplatform also provides an HTTP client for Android, iOS, and desktop, making it useful for sharing networking code across a Kotlin Multiplatform project.

## Quick start

```bash
# Use the Ktor project generator at https://start.ktor.io
# Or generate with IntelliJ IDEA plugin
```

```kotlin
// build.gradle.kts
plugins {
    kotlin("jvm") version "2.0.0"
    id("io.ktor.plugin") version "2.3.x"
    kotlin("plugin.serialization") version "2.0.0"
}

dependencies {
    implementation("io.ktor:ktor-server-core-jvm")
    implementation("io.ktor:ktor-server-netty-jvm")
    implementation("io.ktor:ktor-server-content-negotiation-jvm")
    implementation("io.ktor:ktor-serialization-kotlinx-json-jvm")
}
```

```kotlin
// src/main/kotlin/Application.kt
import io.ktor.server.application.*
import io.ktor.server.engine.*
import io.ktor.server.netty.*
import io.ktor.server.plugins.contentnegotiation.*
import io.ktor.server.response.*
import io.ktor.server.routing.*
import io.ktor.serialization.kotlinx.json.*
import kotlinx.serialization.Serializable

@Serializable
data class Post(val id: Int, val title: String, val body: String)

val posts = mutableListOf<Post>()

fun main() {
    embeddedServer(Netty, port = 8080) {
        install(ContentNegotiation) { json() }

        routing {
            get("/posts") {
                call.respond(posts)
            }
            post("/posts") {
                val post = call.receive<Post>()
                posts.add(post.copy(id = posts.size + 1))
                call.respond(HttpStatusCode.Created, post)
            }
        }
    }.start(wait = true)
}
```

## When to use

Ktor is the best Kotlin-native web framework choice — its coroutine-first design aligns perfectly with Kotlin idioms and avoids the Spring Boot overhead. Use it for new Kotlin microservices where you want a lightweight footprint and clean coroutine code. For teams already invested in Spring's ecosystem (Spring Security, Spring Data, Spring Cloud), Spring Boot with Kotlin is a lower-migration path. Ktor's multiplatform HTTP client is particularly valuable in Kotlin Multiplatform projects.
