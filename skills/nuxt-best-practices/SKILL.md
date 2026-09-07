---
name: nuxt-best-practices
description: Nuxt 3 architecture, SSR, hybrid rendering, Nitro server routes, auto-imports, data fetching, and SEO optimization.
---

# Nuxt 3 Best Practices Guide

This skill provides production patterns, performance recommendations, and architectural principles for Nuxt 3 applications.

---

## 1. Data Fetching: `useFetch` vs `$fetch` vs `useAsyncData`

### When to Use What
- **`useFetch(url, options)`**:
  - The default for page/component data fetching.
  - Automatically deduplicates requests between SSR and client hydration.
  - Generates unique cache keys automatically based on URL and options.

- **`useAsyncData(key, handler)`**:
  - Use when wrapping complex async logic, multiple API calls, or third-party SDK calls.
  - Always provide a unique explicit key to prevent hydration mismatches.

- **`$fetch(url, options)`**:
  - Use **only** in client-side event handlers (form submissions, click actions) or inside Nitro server routes.
  - **NEVER** use `$fetch` directly in top-level `<script setup>` in SSR mode without wrapping in `useAsyncData`, as it triggers duplicate network calls (once on the server and once again on the client).

```vue
<script setup lang="ts">
// Good: SSR-safe with caching and reactive params
const page = ref(1)
const { data: posts, status, error, refresh } = await useFetch('/api/posts', {
  query: { page },
  lazy: false,
  transform: (res) => res.items
})

// Good: Action handler uses $fetch
async function createPost(newPost: PostPayload) {
  await $fetch('/api/posts', {
    method: 'POST',
    body: newPost
  })
  refresh() // Re-fetch the query
}
</script>
```

---

## 2. Server API Routes (Nitro Engine)

Store server endpoints in `server/api/` or `server/routes/`. They run with zero-bundle overhead on the client:

```ts
// server/api/posts/[id].get.ts
export default defineEventHandler(async (event) => {
  const id = getRouterParam(event, 'id')
  const query = getQuery(event)

  if (!id) {
    throw createError({
      statusCode: 400,
      statusMessage: 'ID parameter is required'
    })
  }

  const post = await database.getPostById(id)
  if (!post) {
    throw createError({
      statusCode: 404,
      statusMessage: 'Post not found'
    })
  }

  return post
})
```

---

## 3. Hybrid Rendering & Route Rules

Configure rendering strategies per route in `nuxt.config.ts`:

```ts
// nuxt.config.ts
export default defineNuxtConfig({
  compatibilityDate: '2024-04-03',
  
  routeRules: {
    // Static / Pre-rendered at build time
    '/': { prerender: true },
    '/about': { prerender: true },
    
    // Incremental Static Regeneration / SWR (cache on edge for 1 hour)
    '/blog/**': { swr: 3600 },
    
    // Client-side only (SPA mode) for admin dashboards
    '/admin/**': { ssr: false },
    
    // Reverse proxy API requests to backend
    '/backend-api/**': { proxy: 'https://api.example.com/**' },
    
    // Security headers
    '/**': {
      headers: {
        'X-Frame-Options': 'DENY',
        'X-Content-Type-Options': 'nosniff'
      }
    }
  }
})
```

---

## 4. SEO & Meta Management

Use `useSeoMeta` for type-safe, performant meta tags:

```vue
<script setup lang="ts">
const { data: article } = await useFetch(`/api/articles/${route.params.slug}`)

useSeoMeta({
  title: () => article.value?.title ?? 'Default Title',
  description: () => article.value?.summary,
  ogTitle: () => article.value?.title,
  ogDescription: () => article.value?.summary,
  ogImage: () => article.value?.coverImage,
  twitterCard: 'summary_large_image'
})
</script>
```

---

## 5. Hydration & State Rules
1. **Prevent Hydration Mismatch**: Avoid rendering date timestamps (`new Date().toLocaleTimeString()`), random numbers, or browser-only APIs (`window`, `localStorage`) directly in template without `<ClientOnly>` wrapper.
2. **State Sharing Across SSR**: Use `useState<T>('key', () => initialValue)` instead of module-level variables. Module-level variables are shared across requests in Node.js, causing data leaks between users!
