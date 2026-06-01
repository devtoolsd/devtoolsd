---
name: Bootstrap
slug: bootstrap
language: javascript
description: Responsive CSS component framework — grid system, pre-built components, and the web's most widely used frontend toolkit.
logo: https://upload.wikimedia.org/wikipedia/commons/b/b2/Bootstrap_logo.svg
website: https://getbootstrap.com
github: twbs/bootstrap
year: 2011
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [css, frontend, responsive, components, ui, grid, jquery]
related_frameworks: [tailwindcss]
features:
  - "12-column responsive grid with flexbox and CSS Grid utilities"
  - "Pre-built components: navbar, modal, carousel, tabs, toast, offcanvas"
  - "Form controls and validation styles out of the box"
  - "Customisable via Sass variables — change colors, spacing, and breakpoints"
  - "Dark mode support via `data-bs-theme` attribute (Bootstrap 5.3+)"
  - "Bootstrap Icons — 2000+ open-source SVG icons"
  - "JavaScript plugins (dropdowns, modals, tooltips) with no jQuery required"
  - "CDN and npm distribution — works with or without a build tool"
install:
  npm: "npm install bootstrap"
  cdn: '<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5/dist/css/bootstrap.min.css">'
---

Bootstrap's 12-column grid and pre-built components (navbar, modal, card, form) allowed developers to build responsive sites without design skills. It dominated web development in the 2010s and its approach of utility classes influenced virtually every CSS framework that followed. Bootstrap 5 dropped jQuery, added CSS custom properties throughout, and introduced dark mode support. It remains the most widely used CSS framework by sheer install volume.

## Quick start

```html
<!DOCTYPE html>
<html lang="en" data-bs-theme="light">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5/dist/css/bootstrap.min.css">
  <title>Bootstrap Demo</title>
</head>
<body>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container">
      <a class="navbar-brand" href="#">MySite</a>
    </div>
  </nav>

  <div class="container mt-4">
    <div class="row g-3">
      <div class="col-md-4">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">Some quick example text.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

## When to use

Bootstrap is the fastest way to get a professional-looking responsive UI without writing CSS from scratch. It's ideal for internal tools, admin panels, and projects where design consistency matters more than a unique look. For highly customised designs, Tailwind CSS gives more control at the cost of more CSS to write. If you're using a component-based framework (React/Vue), shadcn/ui or Radix UI might be a better fit than Bootstrap's jQuery-heritage component model.
