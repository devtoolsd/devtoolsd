---
name: Phoenix
slug: phoenix
language: elixir
description: Productive Elixir web framework — real-time channels, LiveView, and Rails-like conventions on the fault-tolerant BEAM VM.
logo: https://upload.wikimedia.org/wikipedia/commons/a/a8/Phoenix_framework_logo.svg
website: https://phoenixframework.org
github: phoenixframework/phoenix
year: 2014
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, elixir, real-time, channels, liveview, websocket, beam]
related_frameworks: [rails, django]
features:
  - "Phoenix Channels — WebSocket connections via the BEAM's concurrency model"
  - "Phoenix LiveView — interactive server-rendered UI without JavaScript"
  - "Ecto ORM — composable, explicit query building with changesets"
  - "Millions of concurrent connections on a single server"
  - "Hot code reloading — update production code with zero downtime"
  - "PubSub system built on the BEAM's message passing"
  - "Telemetry and built-in metrics for observability"
  - "Generators for contexts, schemas, and LiveView components"
install:
  mix: "mix archive.install hex phx_new && mix phx.new my_app"
---

Phoenix combines Rails-like productivity with the BEAM VM's concurrency model. Phoenix Channels (WebSockets) handle millions of connections on a single server. Phoenix LiveView enables rich, interactive server-rendered UIs without writing JavaScript — state lives on the server and diffs are pushed to the browser. The BEAM's fault-tolerant process model means Phoenix apps recover from errors without bringing down the whole server.

## Quick start

```bash
mix archive.install hex phx_new
mix phx.new my_app --database postgresql
cd my_app
mix ecto.create
mix phx.server
```

```elixir
# lib/my_app_web/controllers/post_controller.ex
defmodule MyAppWeb.PostController do
  use MyAppWeb, :controller
  alias MyApp.Blog
  alias MyApp.Blog.Post

  def index(conn, _params) do
    posts = Blog.list_posts()
    render(conn, :index, posts: posts)
  end

  def create(conn, %{"post" => post_params}) do
    case Blog.create_post(post_params) do
      {:ok, post} ->
        conn
        |> put_flash(:info, "Post created.")
        |> redirect(to: ~p"/posts/#{post}")

      {:error, %Ecto.Changeset{} = changeset} ->
        render(conn, :new, changeset: changeset)
    end
  end
end
```

```elixir
# LiveView example — live counter without JavaScript
defmodule MyAppWeb.CounterLive do
  use MyAppWeb, :live_view

  def mount(_params, _session, socket) do
    {:ok, assign(socket, count: 0)}
  end

  def handle_event("increment", _, socket) do
    {:noreply, update(socket, :count, &(&1 + 1))}
  end

  def render(assigns) do
    ~H"""
    <div>
      <p>Count: <%= @count %></p>
      <button phx-click="increment">Increment</button>
    </div>
    """
  end
end
```

## When to use

Phoenix is the best choice when you need real-time features (chat, live dashboards, multiplayer), high concurrency, and Rails-like developer productivity. Elixir's BEAM VM provides fault tolerance and scalability that no other stack matches at its level. LiveView eliminates the need for a separate JavaScript frontend for many interactive UIs. The trade-off is learning Elixir and the BEAM model, which is a different programming paradigm than Ruby, Python, or Node.js.
