---
name: Play Framework
slug: play
language: scala
description: Reactive web framework for Scala and Java — stateless, asynchronous, and built on Akka for high-throughput services.
logo: https://upload.wikimedia.org/wikipedia/commons/6/61/Playframework_logo.svg
website: https://playframework.com
github: playframework/playframework
year: 2007
pricing: free
open_source: true
license: Apache-2.0
tool_type: web
tags: [backend, scala, java, reactive, async, rest, akka]
related_frameworks: [spring-boot, akka, vert-x]
features:
  - "Reactive, non-blocking I/O throughout — no thread blocking by default"
  - "Hot reload in development — change code, refresh the browser"
  - "Type-safe routing — routes are checked at compile time"
  - "Twirl template engine — type-safe HTML templates in Scala"
  - "Built on Akka — actor model for concurrent, distributed systems"
  - "Play WS for async HTTP client calls"
  - "Slick or Anorm for database access"
  - "Supports both Scala and Java APIs"
install:
  sbt: "sbt new playframework/play-scala-seed.g8"
---

Play was one of the first JVM frameworks to embrace reactive, non-blocking I/O throughout — no thread blocking, no synchronous calls. Its hot-reload, type-safe routing, and Twirl templates made Scala web development productive. Used at LinkedIn, Walmart, and many data-heavy applications requiring high concurrent throughput. Play 3 is built on Pekko (the Apache fork of Akka).

## Quick start

```bash
sbt new playframework/play-scala-seed.g8
# Follow prompts for project name
cd my-app
sbt run
```

```scala
// app/controllers/PostController.scala
package controllers

import javax.inject._
import play.api._
import play.api.mvc._
import play.api.libs.json._

case class Post(id: Long, title: String, body: String)
object Post { implicit val format: OFormat[Post] = Json.format[Post] }

@Singleton
class PostController @Inject()(val controllerComponents: ControllerComponents)
  extends BaseController {

  private var posts: Seq[Post] = Seq(Post(1, "Hello Play", "Getting started."))

  def list = Action {
    Ok(Json.toJson(posts))
  }

  def create = Action(parse.json) { request =>
    request.body.validate[Post].fold(
      errors => BadRequest(JsError.toJson(errors)),
      post => {
        val newPost = post.copy(id = posts.length + 1)
        posts = posts :+ newPost
        Created(Json.toJson(newPost))
      }
    )
  }
}
```

```
# conf/routes
GET   /posts         controllers.PostController.list
POST  /posts         controllers.PostController.create
```

## When to use

Play Framework suits Scala and Java teams building high-throughput reactive services, especially when already using the Akka/Pekko ecosystem. It's particularly strong for streaming and data-heavy APIs. For most Java teams, Spring Boot is the more practical choice with a larger talent pool. For Scala teams building purely functional services, http4s or ZIO HTTP are more idiomatic. Play's hot-reload and type-safe routing remain developer-friendly advantages.
