---
name: Symfony
slug: symfony
language: php
description: Enterprise-grade PHP framework — reusable components powering Laravel, Drupal, Magento, and countless other PHP projects.
logo: https://upload.wikimedia.org/wikipedia/commons/6/60/Symfony2.svg
website: https://symfony.com
github: symfony/symfony
year: 2005
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [backend, php, enterprise, components, api, fullstack]
related_frameworks: [laravel, codeigniter, slim]
features:
  - "Reusable standalone components — used by Laravel, Drupal, Magento, phpBB"
  - "Dependency injection container with auto-wiring"
  - "Flex recipe system — install bundles with `composer req` and auto-configure"
  - "Doctrine ORM integration — the standard PHP ORM"
  - "Twig templating engine"
  - "API Platform — REST and GraphQL API framework built on Symfony"
  - "Console component for CLI commands"
  - "Messenger component for async jobs and event buses"
install:
  composer: "composer create-project symfony/skeleton my-app"
  symfony: "symfony new my-app --version=lts"
---

Symfony is both a full-stack framework and a collection of standalone PHP components — HttpFoundation, Console, DependencyInjection, EventDispatcher — that form the plumbing of the PHP ecosystem. Laravel, Drupal, Magento, and phpBB are all built on Symfony components. Its long-term support (LTS) releases and strict backward compatibility make it the enterprise PHP choice.

## Quick start

```bash
symfony new my-app --version=lts
cd my-app
symfony serve -d
```

```php
// src/Controller/PostController.php
namespace App\Controller;

use App\Entity\Post;
use App\Repository\PostRepository;
use Doctrine\ORM\EntityManagerInterface;
use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\JsonResponse;
use Symfony\Component\HttpFoundation\Request;
use Symfony\Component\Routing\Annotation\Route;

#[Route('/api/posts')]
class PostController extends AbstractController
{
    #[Route('', methods: ['GET'])]
    public function index(PostRepository $repo): JsonResponse
    {
        return $this->json($repo->findAll());
    }

    #[Route('', methods: ['POST'])]
    public function create(Request $request, EntityManagerInterface $em): JsonResponse
    {
        $data = json_decode($request->getContent(), true);
        $post = new Post();
        $post->setTitle($data['title']);
        $post->setBody($data['body']);
        $em->persist($post);
        $em->flush();
        return $this->json($post, 201);
    }

    #[Route('/{id}', methods: ['GET'])]
    public function show(Post $post): JsonResponse
    {
        return $this->json($post);
    }
}
```

## When to use

Symfony is the right choice for large PHP enterprise applications, complex APIs (via API Platform), and projects that need long-term stability and LTS support. Its component architecture makes it the foundation of the PHP ecosystem — knowing Symfony components gives you insight into Laravel, Drupal, and Sylius. For smaller projects, Laravel's developer experience is faster. For pure REST APIs, API Platform (Symfony-based) is the best PHP option.
