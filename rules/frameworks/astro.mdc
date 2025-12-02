---
description: Astro best practices for content-focused websites with Islands Architecture
globs: ["**/*.astro", "src/pages/**/*", "src/content/**/*"]
alwaysApply: false
---

# Astro Best Practices

## Overview

| Aspect | Recommendation |
|--------|----------------|
| Use Case | Content-focused sites, blogs, docs |
| Default | Zero JS shipped to client |
| Interactive | Islands (React, Vue, Svelte, etc.) |
| Content | Content Collections |

---

## Project Structure

```
src/
├── components/     # .astro and framework components
├── content/        # Content collections (markdown, MDX)
│   └── blog/
│       └── post-1.md
├── layouts/        # Page layouts
├── pages/          # File-based routing
│   ├── index.astro
│   └── blog/
│       └── [slug].astro
├── styles/         # Global styles
└── content.config.ts  # Collection schemas
```

---

## Astro Components

### Basic Component

```astro
---
// Component Script (runs at build time)
interface Props {
  title: string
  description?: string
}

const { title, description = 'Default description' } = Astro.props
const currentYear = new Date().getFullYear()
---

<!-- Component Template -->
<article>
  <h1>{title}</h1>
  <p>{description}</p>
  <footer>© {currentYear}</footer>
</article>

<style>
  /* Scoped by default */
  article {
    padding: 1rem;
  }
</style>
```

### Slots

```astro
---
// Card.astro
interface Props {
  title: string
}

const { title } = Astro.props
---

<div class="card">
  <h2>{title}</h2>
  <slot />  <!-- Default slot -->
  <slot name="footer" />  <!-- Named slot -->
</div>

<!-- Usage -->
<Card title="My Card">
  <p>Card content</p>
  <div slot="footer">Footer content</div>
</Card>
```

---

## Islands Architecture

### Client Directives

```astro
---
import ReactCounter from './Counter.tsx'
import VueModal from './Modal.vue'
---

<!-- Load immediately -->
<ReactCounter client:load />

<!-- Load when visible (lazy) -->
<ReactCounter client:visible />

<!-- Load when idle -->
<ReactCounter client:idle />

<!-- Load on specific media query -->
<VueModal client:media="(max-width: 768px)" />

<!-- Only hydrate client-side (no SSR) -->
<ReactCounter client:only="react" />
```

### When to Use Islands

| Directive | Use Case |
|-----------|----------|
| `client:load` | Critical interactive elements |
| `client:visible` | Below-the-fold components |
| `client:idle` | Low-priority interactivity |
| `client:media` | Mobile/desktop specific |
| No directive | Static content (default) |

---

## Content Collections

### Define Schema

```typescript
// src/content.config.ts
import { defineCollection, z } from 'astro:content'

const blog = defineCollection({
  type: 'content',  // Markdown/MDX
  schema: z.object({
    title: z.string(),
    description: z.string(),
    pubDate: z.date(),
    author: z.string(),
    tags: z.array(z.string()).optional(),
    draft: z.boolean().default(false),
  }),
})

export const collections = { blog }
```

### Create Content

```markdown
---
# src/content/blog/my-post.md
title: "My First Post"
description: "A great post"
pubDate: 2025-01-15
author: "John Doe"
tags: ["astro", "web"]
---

# Hello World

This is my first blog post!
```

### Query Content

```astro
---
// src/pages/blog/index.astro
import { getCollection } from 'astro:content'

const posts = await getCollection('blog', ({ data }) => {
  return data.draft !== true  // Filter out drafts
})

// Sort by date
const sortedPosts = posts.sort(
  (a, b) => b.data.pubDate.valueOf() - a.data.pubDate.valueOf()
)
---

<ul>
  {sortedPosts.map(post => (
    <li>
      <a href={`/blog/${post.slug}`}>{post.data.title}</a>
    </li>
  ))}
</ul>
```

### Dynamic Routes

```astro
---
// src/pages/blog/[slug].astro
import { getCollection, type CollectionEntry } from 'astro:content'

export async function getStaticPaths() {
  const posts = await getCollection('blog')
  return posts.map(post => ({
    params: { slug: post.slug },
    props: { post },
  }))
}

interface Props {
  post: CollectionEntry<'blog'>
}

const { post } = Astro.props
const { Content } = await post.render()
---

<article>
  <h1>{post.data.title}</h1>
  <time>{post.data.pubDate.toLocaleDateString()}</time>
  <Content />
</article>
```

---

## Layouts

### Base Layout

```astro
---
// src/layouts/BaseLayout.astro
interface Props {
  title: string
  description?: string
}

const { title, description } = Astro.props
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width" />
  <meta name="description" content={description} />
  <title>{title}</title>
</head>
<body>
  <header>
    <nav><!-- Navigation --></nav>
  </header>
  <main>
    <slot />
  </main>
  <footer><!-- Footer --></footer>
</body>
</html>
```

### Using Layouts

```astro
---
// src/pages/about.astro
import BaseLayout from '../layouts/BaseLayout.astro'
---

<BaseLayout title="About Us" description="Learn about our company">
  <h1>About Us</h1>
  <p>We build great things.</p>
</BaseLayout>
```

---

## Data Fetching

### At Build Time

```astro
---
// Runs at build time
const response = await fetch('https://api.example.com/data')
const data = await response.json()
---

<ul>
  {data.map(item => <li>{item.name}</li>)}
</ul>
```

### API Routes (SSR)

```typescript
// src/pages/api/hello.ts
import type { APIRoute } from 'astro'

export const GET: APIRoute = async ({ params, request }) => {
  return new Response(JSON.stringify({ message: 'Hello!' }), {
    status: 200,
    headers: { 'Content-Type': 'application/json' }
  })
}

export const POST: APIRoute = async ({ request }) => {
  const body = await request.json()
  // Process data
  return new Response(JSON.stringify({ success: true }))
}
```

---

## Styling

### Scoped Styles (Default)

```astro
<style>
  /* Only applies to this component */
  h1 {
    color: blue;
  }
</style>
```

### Global Styles

```astro
<style is:global>
  /* Applies globally */
  body {
    font-family: system-ui;
  }
</style>
```

### Tailwind CSS

```astro
---
// Tailwind works out of the box after setup
---

<div class="flex items-center gap-4 p-4 bg-gray-100 rounded-lg">
  <h1 class="text-2xl font-bold">Hello</h1>
</div>
```

---

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Adding JS to static content | Only use client directives when needed |
| Using `client:load` everywhere | Use `client:visible` or `client:idle` |
| Not using Content Collections | Structure content with schemas |
| Fetching client-side | Fetch at build time in frontmatter |
| Huge monolithic pages | Break into smaller components |
