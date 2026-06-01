---
name: Ruby on Rails
slug: rails
language: ruby
description: Full-stack web framework that popularised convention over configuration — MVC, ActiveRecord ORM, and developer productivity by default.
logo: https://upload.wikimedia.org/wikipedia/commons/6/62/Ruby_On_Rails_Logo.svg
website: https://rubyonrails.org
github: rails/rails
year: 2004
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, fullstack, mvc, orm, ruby, web, productivity]
related_frameworks: [sinatra, django, laravel]
features:
  - "Convention over configuration — sensible defaults for everything"
  - "ActiveRecord ORM with migrations, validations, and associations"
  - "Scaffolding generates CRUD controllers, views, and models instantly"
  - "Action Cable for WebSockets and Hotwire for live page updates"
  - "Asset pipeline and import maps for JavaScript and CSS"
  - "Built-in testing with Minitest, fixtures, and system tests"
  - "Strong security defaults — CSRF, SQL injection, XSS protection"
  - "Active Job, Action Mailer, and Active Storage included"
install:
  gem: "gem install rails"
  bundler: "bundle add rails"
---

Rails introduced convention over configuration and DRY principles to web development, enabling a full CRUD application in minutes. It powers Shopify, GitHub (historically), and Basecamp. Rails' opinionated defaults — ActiveRecord, Action Cable, Hotwire — cover everything from the database to real-time updates. Its `rails generate` scaffold command remains one of the most productive ways to bootstrap a new resource.

## Quick start

```bash
gem install rails
rails new myapp --database=postgresql
cd myapp
```

```ruby
# Generate a Post scaffold with title and body
rails generate scaffold Post title:string body:text
rails db:migrate
rails server
# Visit http://localhost:3000/posts for full CRUD
```

```ruby
# app/models/post.rb
class Post < ApplicationRecord
  validates :title, presence: true, length: { minimum: 3 }
  has_many :comments, dependent: :destroy
end

# app/controllers/posts_controller.rb (generated)
class PostsController < ApplicationController
  before_action :set_post, only: %i[show edit update destroy]

  def index
    @posts = Post.all.order(created_at: :desc)
  end

  def show; end

  private

  def set_post
    @post = Post.find(params[:id])
  end

  def post_params
    params.require(:post).permit(:title, :body)
  end
end
```

## When to use

Rails is the best choice when you want to ship a full-stack web application quickly with a relational database and you're comfortable with Ruby. Its conventions eliminate decision fatigue on project structure, making it ideal for startups and product teams. For API-only backends, `rails new --api` is a lighter setup. If your team is Python-first, Django offers a similar batteries-included philosophy.
