---
name: CodeIgniter
slug: codeigniter
language: php
description: Lightweight PHP framework with a small footprint — fast to set up, minimal configuration, popular for hosting-constrained environments.
logo: https://upload.wikimedia.org/wikipedia/commons/3/34/Codeigniter.svg
website: https://codeigniter.com
github: codeigniter4/CodeIgniter4
year: 2006
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, php, lightweight, mvc, api, shared-hosting]
related_frameworks: [laravel, symfony, slim]
features:
  - "Tiny footprint — no Composer required for basic usage"
  - "MVC architecture with simple controller-model-view separation"
  - "Query Builder for safe, chainable database access"
  - "Form validation with built-in rules"
  - "RESTful API support with optional authentication filters"
  - "Session handling with database, file, and Redis drivers"
  - "Works on shared hosting without shell access"
  - "Minimal configuration — drop into a PHP host and run"
install:
  composer: "composer create-project codeigniter4/appstarter my-app"
---

CodeIgniter was designed for shared hosting environments where installing packages is difficult — its small footprint and minimal dependencies make it easy to drop into any PHP host. CodeIgniter 4 is a modern rewrite with namespaces, type hints, and an async-ready foundation while retaining the lightweight philosophy that made version 3 popular.

## Quick start

```bash
composer create-project codeigniter4/appstarter my-app
cd my-app
php spark serve
```

```php
// app/Controllers/Posts.php
namespace App\Controllers;

use CodeIgniter\RESTful\ResourceController;

class Posts extends ResourceController
{
    protected $modelName = 'App\Models\PostModel';
    protected $format    = 'json';

    public function index()
    {
        return $this->respond($this->model->findAll());
    }

    public function show($id = null)
    {
        $post = $this->model->find($id);
        return $post
            ? $this->respond($post)
            : $this->failNotFound("Post $id not found");
    }

    public function create()
    {
        $data = $this->request->getJSON(true);
        if (!$this->model->insert($data)) {
            return $this->failValidationErrors($this->model->errors());
        }
        return $this->respondCreated($data);
    }
}
```

```php
// app/Models/PostModel.php
namespace App\Models;

use CodeIgniter\Model;

class PostModel extends Model
{
    protected $table      = 'posts';
    protected $allowedFields = ['title', 'body'];
    protected $useTimestamps = true;
}
```

## When to use

CodeIgniter is a good choice when deploying to shared hosting that doesn't support Composer or CLI access, or when you need a PHP framework with the smallest possible footprint. For modern PHP development with a full ecosystem, Laravel is the better choice. CodeIgniter's quick setup makes it useful for small internal tools where the overhead of a larger framework isn't justified.
