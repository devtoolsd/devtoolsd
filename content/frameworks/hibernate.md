---
name: Hibernate
slug: hibernate
language: java
description: Java ORM framework — maps Java objects to relational database tables with HQL, caching, and lazy loading.
logo: https://upload.wikimedia.org/wikipedia/commons/2/22/Hibernate_logo_a.png
website: https://hibernate.org
github: hibernate/hibernate-orm
year: 2001
pricing: free
open_source: true
license: LGPL-2.1
tool_type: data
tags: [orm, database, java, jpa, sql, persistence, caching]
related_frameworks: [spring-boot, quarkus]
features:
  - "JPA reference implementation — standard Java persistence API"
  - "HQL/JPQL — database-agnostic query language over your object model"
  - "Automatic schema generation and migration support via `hbm2ddl`"
  - "First-level cache (session-scoped) and second-level cache (EhCache, Redis)"
  - "Lazy and eager loading strategies for associations"
  - "Criteria API for type-safe, programmatic queries"
  - "Support for PostgreSQL, MySQL, Oracle, SQL Server, H2, and more"
  - "Hibernate Validator for bean validation (JSR-380)"
install:
  maven: "<dependency>\n  <groupId>org.hibernate.orm</groupId>\n  <artifactId>hibernate-core</artifactId>\n</dependency>"
  gradle: "implementation 'org.hibernate.orm:hibernate-core:6.x'"
---

Hibernate is the reference implementation of JPA (Java Persistence API) and the standard ORM for Java applications. Its query language (HQL/JPQL) is database-agnostic, and its second-level cache with EhCache or Redis reduces database load dramatically. Spring Boot's Spring Data JPA is backed by Hibernate by default — if you use Spring Boot, you're already using Hibernate.

## Quick start

```xml
<!-- pom.xml — Spring Boot project -->
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
  <groupId>com.h2database</groupId>
  <artifactId>h2</artifactId>
  <scope>runtime</scope>
</dependency>
```

```java
// Post.java — JPA Entity
@Entity
@Table(name = "posts")
public class Post {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String title;

    @Column(columnDefinition = "TEXT")
    private String body;

    @CreationTimestamp
    private LocalDateTime createdAt;

    // One post has many comments
    @OneToMany(mappedBy = "post", cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    private List<Comment> comments = new ArrayList<>();

    // getters + setters
}

// PostRepository.java — Spring Data JPA
public interface PostRepository extends JpaRepository<Post, Long> {
    List<Post> findByTitleContainingIgnoreCase(String keyword);

    @Query("SELECT p FROM Post p WHERE SIZE(p.comments) > :count")
    List<Post> findPostsWithManyComments(@Param("count") int count);
}
```

## When to use

Hibernate is the de-facto Java ORM — if you're using Spring Boot with a relational database, you're almost certainly using Hibernate through Spring Data JPA. Its caching, lazy loading, and HQL make it suitable for complex domain models. For read-heavy workloads where you want fine control over SQL, jOOQ is a type-safe SQL builder that complements or replaces Hibernate. For microservices with simpler data models, Spring Data JDBC (without Hibernate) has less overhead.
