---
name: Gatsby
slug: gatsby
language: javascript
description: React-based static site generator with a GraphQL data layer — pioneered the JAMstack approach for content-heavy websites.
logo: https://upload.wikimedia.org/wikipedia/commons/d/d6/Gatsby.png
website: https://gatsbyjs.com
github: gatsbyjs/gatsby
year: 2015
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [static, react, graphql, jamstack, frontend, cms, performance]
related_frameworks: [nextjs, astro, remix, react]
features:
  - "GraphQL data layer — query CMS, APIs, and files with a unified API"
  - "Rich plugin ecosystem for images, PWA, CMS integrations"
  - "Incremental builds — only rebuild pages that changed"
  - "Gatsby Image — automatic lazy loading, WebP, and responsive sizes"
  - "Partial hydration (Gatsby 5) — only hydrate components that need JS"
  - "Slice API for shared UI sections built once and inserted across pages"
  - "Works with Contentful, Sanity, WordPress, and most headless CMSes"
  - "Built-in PWA manifest and offline plugin"
install:
  npm: "npm init gatsby"
  npx: "npx gatsby new my-site"
---

Gatsby popularised the idea of pulling content from CMSes, APIs, and files into a unified GraphQL layer at build time, then shipping static HTML and JavaScript. Its plugin ecosystem handles image optimisation, PWA features, and dozens of CMS integrations. Gatsby 5 added partial hydration and Slice APIs for large-scale content sites. While Next.js has taken the lion's share of the React framework market, Gatsby remains a strong choice for content-heavy sites with complex data sourcing needs.

## Quick start

```bash
npm init gatsby my-site
cd my-site
npm run develop
```

```javascript
// gatsby-config.js
module.exports = {
  siteMetadata: {
    title: 'My Gatsby Site',
    siteUrl: 'https://mysite.com',
  },
  plugins: [
    'gatsby-plugin-image',
    'gatsby-plugin-sharp',
    'gatsby-transformer-sharp',
    {
      resolve: 'gatsby-source-filesystem',
      options: { name: 'blog', path: `${__dirname}/content/blog` },
    },
    'gatsby-transformer-remark',
  ],
}
```

```jsx
// src/pages/index.jsx
import { graphql } from 'gatsby'

export default function Home({ data }) {
  return (
    <main>
      <h1>{data.site.siteMetadata.title}</h1>
      <ul>
        {data.allMarkdownRemark.nodes.map(post => (
          <li key={post.id}>
            <a href={post.frontmatter.slug}>{post.frontmatter.title}</a>
          </li>
        ))}
      </ul>
    </main>
  )
}

export const query = graphql`
  query {
    site { siteMetadata { title } }
    allMarkdownRemark(sort: { frontmatter: { date: DESC } }) {
      nodes {
        id
        frontmatter { title slug date }
      }
    }
  }
`
```

## When to use

Gatsby is best when you need a React-based static site with complex data sourcing from multiple CMSes or APIs, and your team is comfortable with GraphQL. For simpler content sites with less data complexity, Astro ships less JavaScript by default. For sites that need both static generation and server-side rendering, Next.js has a broader feature set. Gatsby's plugin ecosystem remains valuable for CMS-heavy projects.
