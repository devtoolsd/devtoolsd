---
name: Slim
slug: slim
language: php
description: Micro-framework for PHP APIs and web apps — PSR-7 middleware stack, fast routing, and minimal overhead.
website: https://slimframework.com
github: slimphp/Slim
year: 2011
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, php, micro, api, rest, psr-7, middleware]
related_frameworks: [laravel, symfony, lumen]
features:
  - "PSR-7 HTTP messages and PSR-15 middleware — interoperable with any PSR-compatible library"
  - "Fast router with URL parameters, route groups, and named routes"
  - "PSR-11 dependency injection container"
  - "Error handling and 404/405 responses"
  - "Middleware stack — add logging, auth, CORS, rate limiting"
  - "Twig, Smarty, or plain PHP templates"
  - "Works on PHP 7.4+ with minimal configuration"
  - "Ideal for microservices and serverless PHP (AWS Lambda, GCP)"
install:
  composer: "composer require slim/slim slim/psr7"
---

Slim follows PHP-FIG standards (PSR-7, PSR-15) for its HTTP message and middleware interfaces. Its tiny core — router, DI container, error handling — is ideal for PHP microservices and REST APIs where Laravel or Symfony would be overkill.

## Quick start

```bash
composer require slim/slim slim/psr7
```

```php
<?php
// public/index.php
use Slim\Factory\AppFactory;
use Psr\Http\Message\ResponseInterface as Response;
use Psr\Http\Message\ServerRequestInterface as Request;

require __DIR__ . '/../vendor/autoload.php';

$app = AppFactory::create();
$app->addErrorMiddleware(true, true, true);

$posts = [];

$app->get('/posts', function (Request $request, Response $response) use (&$posts) {
    $response->getBody()->write(json_encode($posts));
    return $response->withHeader('Content-Type', 'application/json');
});

$app->post('/posts', function (Request $request, Response $response) use (&$posts) {
    $data = (array) $request->getParsedBody();
    $post = array_merge(['id' => count($posts) + 1], $data);
    $posts[] = $post;
    $response->getBody()->write(json_encode($post));
    return $response->withHeader('Content-Type', 'application/json')
                    ->withStatus(201);
});

$app->get('/posts/{id}', function (Request $request, Response $response, array $args) use (&$posts) {
    $post = array_values(array_filter($posts, fn($p) => $p['id'] == $args['id']))[0] ?? null;
    if (!$post) return $response->withStatus(404);
    $response->getBody()->write(json_encode($post));
    return $response->withHeader('Content-Type', 'application/json');
});

$app->run();
```

## When to use

Slim is the best choice for PHP REST APIs and microservices that need to stay lightweight. Its PSR compliance means any PSR-compatible library (Doctrine DBAL, Monolog, League/OAuth2) integrates without friction. For a full-featured PHP application with ORM, auth, and templating, Laravel is more productive. For pure API backends where you want to assemble your own stack from composer packages, Slim is the clean foundation.
