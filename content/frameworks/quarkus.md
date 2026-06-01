---
name: Quarkus
slug: quarkus
language: java
description: Kubernetes-native Java framework — fast startup, low memory footprint, native compilation via GraalVM.
logo: https://upload.wikimedia.org/wikipedia/commons/3/31/Quarkus_Logo.svg
website: https://quarkus.io
github: quarkusio/quarkus
year: 2019
pricing: free
open_source: true
license: Apache-2.0
tool_type: web
tags: [backend, java, kubernetes, cloud-native, native, graalvm, microservices]
related_frameworks: [spring-boot, micronaut, vert-x]
features:
  - "Native compilation with GraalVM — starts in milliseconds, uses ~50MB RAM"
  - "Live reload in dev mode — code changes are hot-reloaded automatically"
  - "Unified configuration via `application.properties`"
  - "Panache ORM — simplified Hibernate with Active Record pattern"
  - "Reactive and imperative programming models in the same framework"
  - "Dev Services — automatically starts databases and brokers in dev mode"
  - "Extensions for JPA, Kafka, Redis, gRPC, REST, and 200+ more"
  - "Mutiny for reactive streams — `Uni<T>` and `Multi<T>`"
install:
  maven: "mvn io.quarkus.platform:quarkus-maven-plugin:create -DprojectGroupId=com.example"
  quarkus: "quarkus create app com.example:my-app"
---

Quarkus was built for containers — it starts in milliseconds and uses a fraction of the memory of traditional Spring Boot apps when compiled to native with GraalVM. It is developer-friendly with live reload, unified configuration, and familiar extensions for JPA, RESTEasy, Kafka, and more. In JVM mode it still outperforms Spring Boot; in native mode it rivals Go and Rust for cold-start times.

## Quick start

```bash
# Using Quarkus CLI
quarkus create app com.example:my-api \
  --extension='resteasy-reactive-jackson,hibernate-orm-panache,jdbc-postgresql'
cd my-api
quarkus dev
```

```java
// src/main/java/com/example/Post.java
@Entity
public class Post extends PanacheEntity {
    public String title;
    public String body;

    public static List<Post> findPublished() {
        return list("published", true);
    }
}

// src/main/java/com/example/PostResource.java
@Path("/posts")
@Produces(MediaType.APPLICATION_JSON)
@Consumes(MediaType.APPLICATION_JSON)
public class PostResource {

    @GET
    public List<Post> list() {
        return Post.listAll();
    }

    @POST
    @Transactional
    public Response create(Post post) {
        post.persist();
        return Response.status(Response.Status.CREATED).entity(post).build();
    }

    @GET
    @Path("/{id}")
    public Post get(@PathParam("id") Long id) {
        return Post.findById(id);
    }
}
```

```bash
# Build a native executable
quarkus build --native
# Run: ./target/my-api-1.0.0-SNAPSHOT-runner (starts in ~20ms)
```

## When to use

Quarkus is the best choice for Java microservices deployed in containers or serverless where startup time and memory footprint matter. Its Dev Services (auto-starting databases) and live reload make the developer experience excellent. Compared to Micronaut, Quarkus has broader extension coverage and a more active community. For teams with existing Spring Boot codebases, migration is non-trivial — Quarkus is best for greenfield containerised services.
