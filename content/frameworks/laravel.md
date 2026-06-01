---
name: Laravel
slug: laravel
language: php
description: Elegant PHP web framework with expressive syntax, an ORM, queue system, and rich ecosystem.
logo: https://upload.wikimedia.org/wikipedia/commons/9/9a/Laravel.svg
website: https://laravel.com
github: laravel/laravel
year: 2011
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [web, php, orm, eloquent, artisan, mvc, backend]
related_frameworks: [symfony, codeigniter]
features:
  - "Eloquent ORM — ActiveRecord-style models with fluent query builder"
  - "Artisan CLI for generating models, controllers, migrations, and more"
  - "Blade templating engine with components and directives"
  - "Laravel Sanctum and Passport for API token and OAuth authentication"
  - "Queues, jobs, and event broadcasting out of the box"
  - "Laravel Horizon for Redis queue monitoring"
  - "Vite integration for modern frontend asset bundling"
  - "Livewire for reactive UI without writing JavaScript"
install:
  composer: "composer create-project laravel/laravel my-app"
  laravel: "laravel new my-app"
---

Laravel brings developer-friendly conventions to PHP with Eloquent ORM, Blade templating, Artisan CLI, and a massive ecosystem of first-party packages. It's the most popular PHP framework and regularly tops developer satisfaction surveys. Laravel's expressive syntax — fluent query builder, route closures, collection helpers — makes PHP development feel modern. The ecosystem includes Forge (server provisioning), Vapor (serverless), Livewire (reactive UI), and Inertia.js (Vue/React SPA adapter).

## Quick start

```bash
composer create-project laravel/laravel my-app
cd my-app
cp .env.example .env
php artisan key:generate
php artisan serve
```

```php
// Generate a resource controller + model + migration
php artisan make:model Post -mcr

// database/migrations/xxxx_create_posts_table.php
Schema::create('posts', function (Blueprint $table) {
    $table->id();
    $table->string('title');
    $table->text('body');
    $table->timestamps();
});

php artisan migrate
```

```php
// app/Models/Post.php
class Post extends Model
{
    protected $fillable = ['title', 'body'];

    public function scopeRecent($query)
    {
        return $query->orderBy('created_at', 'desc');
    }
}

// routes/web.php
Route::get('/posts', function () {
    return view('posts.index', [
        'posts' => Post::recent()->paginate(15),
    ]);
});

Route::post('/posts', function (Request $request) {
    $data = $request->validate([
        'title' => 'required|min:3',
        'body'  => 'required',
    ]);
    Post::create($data);
    return redirect('/posts');
});
```

## When to use

Laravel is the best choice for PHP applications — whether full-stack web apps, REST APIs, or admin panels. Its Eloquent ORM and Artisan CLI keep PHP productive and expressive. If you need an ultra-lightweight PHP API, Slim or Lumen are options. If your team uses Vue, Inertia.js bridges Laravel and Vue seamlessly without a separate API layer.
