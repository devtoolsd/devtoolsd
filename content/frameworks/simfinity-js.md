---
name: Simfinity.js
slug: simfinity-js
language: javascript

description: Node.js framework that generates GraphQL APIs, relationships and database storage from GraphQL object types, with MongoDB or PostgreSQL adapters.
website: https://simtlix.github.io/simfinity.js/
github: simtlix/simfinity.js

pricing: free
open_source: true
license: Apache-2.0
tool_type: web

tags: [backend, nodejs, graphql, mongodb, postgresql, database, api]
features:
  - "Queries, CRUD mutations and storage mappings generated from GraphQLObjectType definitions"
  - "Relationship fields and nested mutations"
  - "Separate MongoDB/Mongoose and native PostgreSQL adapters"
  - "Validation, lifecycle hooks and authorization rules"
  - "Optional MCP integration for exposing selected API operations as tools"
install:
  npm: "npm install @simtlix/simfinity-postgres graphql"
---

Simfinity.js uses GraphQL object types as the starting point for a Node.js backend. Register the types and describe their relationships to generate queries, CRUD mutations and database storage mappings. Validation, lifecycle hooks and authorization rules provide extension points for application behavior.

Choose `@simtlix/simfinity-postgres` for PostgreSQL or `@simtlix/simfinity-js` for MongoDB/Mongoose. The PostgreSQL adapter uses native tables, UUIDs and foreign keys without a Mongoose dependency. The optional `@simtlix/simfinity-mcp` package exposes selected operations as MCP tools.

## Getting started

The [documentation](https://simtlix.github.io/simfinity.js/) includes runnable starters and examples of nested mutations. The [PostgreSQL guide](https://simtlix.github.io/simfinity.js/guide/postgresql.html) covers connection setup and database initialization.

Authentication and trusted request context remain the application's responsibility. MongoDB generated mutations require a replica set or sharded cluster for transaction support. See the [compatibility guide](https://simtlix.github.io/simfinity.js/compatibility.html) for runtime and database requirements.
