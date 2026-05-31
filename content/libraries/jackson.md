---
name: Jackson
slug: jackson
language: java
description: High-performance JSON processor for Java — object mapping, streaming API, data binding, and a rich module ecosystem.
website: https://github.com/FasterXML/jackson
github: FasterXML/jackson-databind
year: 2009
pricing: free
open_source: true
license: Apache-2.0
library_type: serialization
tags: [json, serialization, java, rest, data-binding, spring]
frameworks: [spring-boot, quarkus, micronaut]
related_libraries: [guava]
---

Jackson is the standard JSON library for Java. Its `ObjectMapper` converts between JSON and POJOs with annotated field control (`@JsonProperty`, `@JsonIgnore`). Spring Boot auto-configures Jackson as the default HTTP message converter; Quarkus and Micronaut both support it out of the box.
