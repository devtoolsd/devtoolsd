---
name: Django
slug: django
language: python
description: Batteries-included Python web framework — ORM, admin panel, auth, and routing out of the box.
logo: https://upload.wikimedia.org/wikipedia/commons/7/75/Django_logo.svg
website: https://djangoproject.com
github: django/django
year: 2005
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: web
tags: [web, orm, mvc, rest, python, backend, batteries-included]
related_frameworks: [flask, fastapi, rails]
features:
  - "Batteries included — ORM, admin panel, authentication, and routing in a single package"
  - "Powerful ORM with migrations, querysets, and relationship modeling"
  - "Auto-generated admin interface from your model definitions"
  - "Built-in user authentication, permissions, and session management"
  - "Template engine with inheritance and custom tags"
  - "Class-based and function-based views"
  - "Strong security defaults — CSRF, XSS, SQL injection protection"
  - "Mature ecosystem with 20+ years of production use"
install:
  pip: "pip install django"
  pipx: "pipx install django"
---

Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Its "batteries included" philosophy means you get an ORM, an admin panel, authentication, URL routing, a template engine, and security middleware all in one package — no hunting for third-party libraries for the basics. It powers Instagram, Disqus, Mozilla, and thousands of data-driven applications.

## Quick start

```bash
# Create a new project
django-admin startproject mysite
cd mysite

# Create an app
python manage.py startapp blog

# Run migrations
python manage.py migrate

# Start the development server
python manage.py runserver
```

```python
# blog/models.py
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=200)
    body = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title

# blog/views.py
from django.shortcuts import render
from .models import Post

def post_list(request):
    posts = Post.objects.order_by('-created_at')
    return render(request, 'blog/post_list.html', {'posts': posts})

# mysite/urls.py
from django.urls import path
from blog import views

urlpatterns = [
    path('', views.post_list, name='post-list'),
]
```

## When to use

Django is the right choice when you need a full-featured web application with a relational database — CMS platforms, admin-heavy internal tools, REST APIs backed by PostgreSQL. It trades flexibility for convention: if your project fits the "model + view + template" pattern, Django will get you to production faster than any other Python framework. For microservices or pure async workloads, consider FastAPI or Starlette instead.
