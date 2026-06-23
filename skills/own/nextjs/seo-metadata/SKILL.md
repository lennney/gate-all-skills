---
name: seo-metadata
description: Next.js SEO patterns — Metadata API, Open Graph, sitemap, robots, and structured data. Use when setting up SEO for a site, adding meta tags, or generating sitemaps.
---

# SEO & Metadata (Next.js)

Practical SEO setup for Next.js App Router.

## 1. Metadata API

Export `metadata` or `generateMetadata` from any layout or page:

```tsx
// src/app/layout.tsx — Root metadata (static)
import type { Metadata } from "next"

export const metadata: Metadata = {
  title: {
    default: "My App",           // fallback if no child title
    template: "%s | My App",     // child title gets inserted: "About | My App"
  },
  description: "Description for search results",
  openGraph: {
    title: "My App",
    description: "OG description",
    url: "https://example.com",
    siteName: "My App",
    images: [{ url: "/og.png", width: 1200, height: 630 }],
    locale: "en_US",
    type: "website",
  },
  twitter: {
    card: "summary_large_image",
    title: "My App",
    description: "Twitter description",
    images: ["/og.png"],
  },
  robots: {
    index: true,
    follow: true,
  },
}
```

## 2. Dynamic Metadata per Page

```tsx
// src/app/blog/[slug]/page.tsx — Dynamic metadata
export async function generateMetadata({ params }: Props): Promise<Metadata> {
  const post = await getPost(params.slug)
  return {
    title: post.title,
    description: post.excerpt,
    openGraph: {
      title: post.title,
      description: post.excerpt,
      images: [post.ogImage],
    },
  }
}
```

## 3. Sitemap

```tsx
// src/app/sitemap.ts
import type { MetadataRoute } from "next"

export default async function sitemap(): Promise<MetadataRoute.Sitemap> {
  const posts = await getPosts()  // fetch your content

  const staticPages = [
    { url: "https://example.com", lastModified: new Date(), priority: 1 },
    { url: "https://example.com/about", lastModified: new Date(), priority: 0.8 },
  ]

  const postPages = posts.map((post) => ({
    url: `https://example.com/blog/${post.slug}`,
    lastModified: post.updatedAt,
    priority: 0.6,
  }))

  return [...staticPages, ...postPages]
}
```

## 4. Robots

```tsx
// src/app/robots.ts
import type { MetadataRoute } from "next"

export default function robots(): MetadataRoute.Robots {
  return {
    rules: {
      userAgent: "*",
      allow: "/",
      disallow: "/api/",
    },
    sitemap: "https://example.com/sitemap.xml",
  }
}
```

## 5. JSON-LD Structured Data

```tsx
// src/app/blog/[slug]/page.tsx
export default function BlogPost({ params }: Props) {
  const post = await getPost(params.slug)

  const jsonLd = {
    "@context": "https://schema.org",
    "@type": "Article",
    headline: post.title,
    description: post.excerpt,
    author: { "@type": "Person", name: post.author },
    datePublished: post.createdAt,
    image: post.ogImage,
  }

  return (
    <>
      <script
        type="application/ld+json"
        dangerouslySetInnerHTML={{ __html: JSON.stringify(jsonLd) }}
      />
      <article>{/* content */}</article>
    </>
  )
}
```

## Quick Reference

| File | Purpose |
|------|---------|
| `layout.tsx` | Root metadata (static) |
| `page.tsx` | Per-page metadata via `generateMetadata` |
| `sitemap.ts` | Sitemap XML generation |
| `robots.ts` | Robots.txt generation |
| `manifest.ts` | PWA manifest |

## Acceptance Criteria

1. Root layout has title template + default description
2. Each page has unique title + OG image
3. Sitemap includes all public pages
4. Robots.txt blocks private paths (/api/, /admin/)
