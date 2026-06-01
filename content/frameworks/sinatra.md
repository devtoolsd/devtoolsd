---
name: Sinatra
slug: sinatra
language: ruby
description: Minimal Ruby DSL for building web applications — route definitions in a handful of lines, no MVC overhead.
website: https://sinatrarb.com
github: sinatra/sinatra
year: 2007
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, micro, ruby, api, rest, dsl, minimal]
related_frameworks: [rails, flask, express]
features:
  - "Route-first DSL — `get '/path' do ... end` is all you need"
  - "Complete API or web app in a single file"
  - "Rack-based — any Rack middleware works"
  - "Template rendering — ERB, Haml, Slim built in"
  - "Modular and classic application styles"
  - "Before/after filters and error handlers"
  - "Built-in session handling"
  - "Minimal overhead — starts in milliseconds"
install:
  gem: "gem install sinatra"
  bundler: "bundle add sinatra puma"
---

Sinatra's domain-specific language maps HTTP verbs and paths to blocks of code — a complete API can fit in a single file. It influenced Flask, Express, and a generation of micro-frameworks. For Ruby services where Rails' weight is unnecessary, Sinatra remains the clean, minimal choice.

## Quick start

```bash
gem install sinatra puma
```

```ruby
# app.rb
require 'sinatra'
require 'json'

posts = []

get '/posts' do
  content_type :json
  posts.to_json
end

get '/posts/:id' do
  content_type :json
  post = posts.find { |p| p[:id] == params[:id].to_i }
  halt 404, { error: 'Not found' }.to_json unless post
  post.to_json
end

post '/posts' do
  content_type :json
  data = JSON.parse(request.body.read, symbolize_names: true)
  post = { id: posts.length + 1, **data }
  posts << post
  status 201
  post.to_json
end
```

```bash
ruby app.rb
# Server running on http://localhost:4567
```

## When to use

Sinatra is the right choice for small Ruby services, internal APIs, and scripts that need HTTP endpoints — anything where the full Rails stack would be overkill. It's particularly popular for microservices, webhooks, and Rack middleware apps. For larger applications with database models, authentication, and complex routing, Rails is a better fit. Flask and Express are the Python and Node.js equivalents.
