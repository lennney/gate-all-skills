---
name: game-landing-seo
description: SEO patterns for game landing pages — VideoGame JSON-LD, OG tags, site config architecture, FAQPage schema. Use when building SEO for a game site, review site, or landing page with structured data.
intent: >-
  Set up comprehensive SEO for game information websites including structured data
  (VideoGame + FAQPage + BreadcrumbList JSON-LD), Open Graph, Twitter cards, sitemap,
  and metadata API. Based on proven patterns from 4 production game sites.
type: pattern
theme: seo
best_for:
  - "Setting up SEO for game review/guide sites"
  - "Multi-site SEO with shared infrastructure"
  - "VideoGame JSON-LD structured data"
---

# Game Landing Page SEO

Proven SEO architecture from 4 production game sites (fatekeeper.org, ihavenochang.com, tbhtaskbarhero.com, soullandawakeningworld.com).

## 1. Site Config Architecture

Keep per-site config separate from SEO logic:

```ts
// src/lib/types.ts
export interface SiteConfig {
  id: string
  domain: string
  name: string
  shortName: string
  tagline: string
  description: string
  keywords: string[]
  ogImage: string
  languages: string[]
  theme: {
    colors: { primary: string; accent: string; background: string; text: string }
    fonts: { heading: string; body: string }
  }
}

// src/lib/site.ts — Single-site config
export function getSiteConfig(): SiteConfig { /* ... */ }
export function getSiteById(id: string): SiteConfig | null { /* ... */ }
```

## 2. Metadata Generator

Centralize metadata generation to keep all pages consistent:

```ts
// src/lib/seo.ts
export function generateSiteMetadata(
  site: SiteConfig,
  overrides?: Partial<Metadata> & {
    pageTitle?: string
    pageDescription?: string
    canonicalPath?: string
  }
): Metadata {
  const title = overrides?.pageTitle
    ? `${overrides.pageTitle} — ${site.name}`
    : `${site.name} — ${site.tagline}`

  return {
    title,
    description: overrides?.pageDescription ?? site.description,
    keywords: site.keywords,
    metadataBase: new URL(`https://${site.domain}`),
    openGraph: {
      title,
      description,
      url: `https://${site.domain}${canonicalPath}`,
      siteName: site.name,
      images: [{ url: site.ogImage, width: 1200, height: 630 }],
    },
    twitter: { card: 'summary_large_image' },
    alternates: {
      canonical: `https://${site.domain}${canonicalPath}`,
    },
  }
}
```

## 3. VideoGame JSON-LD

```tsx
// src/components/StructuredData.tsx
export function StructuredData({ site, data }: { site: SiteConfig; data: GameData }) {
  const videoGame = {
    '@context': 'https://schema.org',
    '@type': 'VideoGame',
    name: data.title,
    description: site.description,
    image: site.ogImage,
    applicationCategory: 'Game',
    operatingSystem: 'Windows',
    author: { '@type': 'Organization', name: data.developer },
    offers: { '@type': 'Offer', price: data.price, priceCurrency: 'USD' },
    aggregateRating: {
      '@type': 'AggregateRating',
      ratingValue: data.score,
      bestRating: 10,
      ratingCount: data.ratingCount,
    },
  }

  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(videoGame) }}
    />
  )
}
```

## 4. FAQPage JSON-LD (from data)

```tsx
// Inside StructuredData.tsx — add when data.faqs exists
const faqPage = data.faqs?.length ? {
  '@context': 'https://schema.org',
  '@type': 'FAQPage',
  mainEntity: data.faqs.map(faq => ({
    '@type': 'Question',
    name: faq.question,
    acceptedAnswer: {
      '@type': 'Answer',
      text: faq.answer,
    },
  })),
} : null
```

## 5. Dynamic Metadata per Page

```tsx
// src/app/review/page.tsx
export function generateMetadata(): Metadata {
  const site = getSiteConfig()
  return generateSiteMetadata(site, {
    pageTitle: 'Review — Pros, Cons & Verdict',
    pageDescription: `Read our honest review of ${site.name}. Pros and cons, gameplay analysis, and final verdict.`,
    canonicalPath: '/review',
  })
}
```

## 6. Sitemap

```tsx
// src/app/sitemap.ts
export default async function sitemap(): Promise<MetadataRoute.Sitemap> {
  const site = getSiteConfig()
  const pages = ['/', '/review', '/guide', '/faq', '/privacy', '/tos']

  return pages.map(path => ({
    url: `https://${site.domain}${path}`,
    lastModified: new Date(),
    changeFrequency: path === '/' ? 'weekly' : 'monthly',
    priority: path === '/' ? 1 : 0.8,
  }))
}
```

## 7. Robots

```tsx
// src/app/robots.ts
export default function robots(): MetadataRoute.Robots {
  const site = getSiteConfig()
  return {
    rules: { userAgent: '*', allow: '/', disallow: '/api/' },
    sitemap: `https://${site.domain}/sitemap.xml`,
  }
}
```

## Acceptance Criteria

1. Each page has unique title + OG image generated via `generateSiteMetadata()`
2. Home page has VideoGame + FAQPage JSON-LD
3. Sitemap includes all public pages with correct priorities
4. Metadata is centralized (not hand-written per page)
