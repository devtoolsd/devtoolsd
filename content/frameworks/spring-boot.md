---
name: Spring Boot
slug: spring-boot
language: java
description: Opinionated Spring framework for production-ready Java microservices — auto-configuration, embedded servers, and a vast ecosystem.
logo: https://upload.wikimedia.org/wikipedia/commons/7/79/Spring_Boot.svg
website: https://spring.io/projects/spring-boot
github: spring-projects/spring-boot
year: 2014
pricing: free
open_source: true
license: Apache-2.0
tool_type: web
tags: [backend, java, microservices, enterprise, rest, dependency-injection]
related_frameworks: [quarkus, micronaut, vert-x]
features:
  - "Auto-configuration — Spring beans wired automatically based on classpath"
  - "Embedded Tomcat, Jetty, or Undertow — no WAR deployment required"
  - "Spring Data JPA for repository-pattern database access"
  - "Spring Security for authentication, authorization, and OAuth2"
  - "Actuator for health checks, metrics, and observability endpoints"
  - "Spring Cloud for distributed systems, service discovery, and config"
  - "Extensive testing support with `@SpringBootTest` and MockMvc"
  - "Native image compilation via GraalVM for fast startup"
install:
  maven: "mvn io.spring.initializr:start.spring.io/starter.zip (or use start.spring.io)"
  gradle: "gradle init (then add Spring Boot plugin)"
---

Spring Boot makes production-grade Spring applications by providing opinionated auto-configuration and embedded Tomcat/Jetty/Undertow servers. It is the dominant Java backend framework — used at Netflix, Airbnb, and virtually every enterprise Java shop. The Spring ecosystem covers security, data access (JPA, Redis, MongoDB), messaging (Kafka, RabbitMQ), batch processing, and cloud-native patterns. The easiest way to start a new project is [start.spring.io](https://start.spring.io).

## Quick start

```bash
# Generate a project at https://start.spring.io
# Select: Maven, Java 21, Spring Web, Spring Data JPA, H2 Database
# Download and unzip, then:
./mvnw spring-boot:run
```

```java
// src/main/java/com/example/demo/Post.java
@Entity
public class Post {
    @Id @GeneratedValue
    private Long id;
    private String title;
    private String body;
    // getters + setters omitted for brevity
}

// PostRepository.java
public interface PostRepository extends JpaRepository<Post, Long> {
    List<Post> findByTitleContaining(String keyword);
}

// PostController.java
@RestController
@RequestMapping("/api/posts")
public class PostController {
    private final PostRepository repo;

    public PostController(PostRepository repo) {
        this.repo = repo;
    }

    @GetMapping
    public List<Post> all() {
        return repo.findAll();
    }

    @PostMapping
    public Post create(@RequestBody Post post) {
        return repo.save(post);
    }

    @GetMapping("/{id}")
    public Post get(@PathVariable Long id) {
        return repo.findById(id)
            .orElseThrow(() -> new ResponseStatusException(HttpStatus.NOT_FOUND));
    }
}
```

## When to use

Spring Boot is the standard choice for Java backend services in enterprise environments — REST APIs, microservices, batch jobs, and event-driven systems. Its maturity, vast ecosystem, and enterprise adoption mean abundant tooling, documentation, and hiring talent. For lower memory footprint and faster startup in containerised environments, consider Quarkus or Micronaut. For Kotlin-first development, Ktor is worth evaluating.
