---
name: ASP.NET Core
slug: aspnet-core
language: csharp
description: Cross-platform, high-performance web framework from Microsoft — REST APIs, MVC, Razor Pages, and real-time with SignalR.
logo: https://upload.wikimedia.org/wikipedia/commons/e/ee/.NET_Core_Logo.svg
website: https://dotnet.microsoft.com/apps/aspnet
github: dotnet/aspnetcore
year: 2016
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, csharp, dotnet, api, rest, mvc, microsoft, cross-platform]
related_frameworks: [blazor]
features:
  - "Minimal APIs — Express-style route handlers for lightweight services"
  - "MVC and Razor Pages for full-stack web applications"
  - "Built-in dependency injection container"
  - "Entity Framework Core for ORM and migrations"
  - "SignalR for real-time WebSocket and SSE communication"
  - "Middleware pipeline — add auth, CORS, compression via `app.Use*()`"
  - "Consistently among the fastest frameworks in TechEmpower benchmarks"
  - "Native AOT compilation for minimal startup time in containers"
install:
  dotnet: "dotnet new webapi -n MyApi && cd MyApi && dotnet run"
---

ASP.NET Core is Microsoft's ground-up rewrite of ASP.NET — cross-platform, cloud-ready, and consistently among the fastest web frameworks in TechEmpower benchmarks. Minimal APIs (introduced in .NET 6) allow Express-style route handlers alongside the full MVC pattern. SignalR provides real-time WebSocket communication, and the built-in DI container wires everything together.

## Quick start

```bash
dotnet new webapi -n MyApi --use-minimal-apis
cd MyApi
dotnet run
```

```csharp
// Program.cs — Minimal API
var builder = WebApplication.CreateBuilder(args);
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

var app = builder.Build();
app.UseSwagger();
app.UseSwaggerUI();

var posts = new List<Post>();

app.MapGet("/posts", () => Results.Ok(posts));

app.MapGet("/posts/{id}", (int id) =>
    posts.FirstOrDefault(p => p.Id == id) is Post post
        ? Results.Ok(post)
        : Results.NotFound());

app.MapPost("/posts", (Post post) => {
    post.Id = posts.Count + 1;
    posts.Add(post);
    return Results.Created($"/posts/{post.Id}", post);
});

app.Run();

record Post(int Id, string Title, string Body);
```

## When to use

ASP.NET Core is the standard choice for .NET teams building web APIs and full-stack applications. Its performance, tooling, and tight Visual Studio integration make it the dominant enterprise .NET backend. Minimal APIs are ideal for microservices; MVC suits larger applications with complex view logic. For .NET teams that want to keep UI logic server-side and avoid JavaScript, Razor Pages and Blazor Server complement it well.
