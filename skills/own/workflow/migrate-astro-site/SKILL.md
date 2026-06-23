---
name: migrate-astro-site
description: 1:1 migration from Astro to Next.js 16 — copy content unchanged, transform syntax only. Use when migrating an Astro static site to Next.js App Router with SSR.
intent: >-
  Migrate an Astro static site to Next.js 16 with SSR, following a proven 11-phase process. 
  Content is copied verbatim (no rewriting), only syntax is converted (class→className, etc.).
  Uses ssr-fatekeeper as the golden template for infrastructure (13 shared components, SEO pipeline, deployment config).
type: workflow
theme: migration
best_for:
  - "Migrating Astro sites to Next.js"
  - "Setting up SSR with preserved SEO"
  - "Multi-site migration with shared template"
---

# Migrate Astro Site → Next.js 16

Migrate an Astro static site to Next.js 16 with SSR, preserving all content and styling 1:1.

## Core Principle

> **Content unchanged, syntax only.** Copy verbatim, transform `class`→`className`, `style` strings→objects. Never rewrite content.

## Phase 0: Check Skeleton State

If `ssr-{slug}` already exists, check for half-baked state:

- [ ] `src/lib/site.ts` — correct domain/id?
- [ ] `src/components/` — all 13 shared components present?
- [ ] `layout.tsx` — uses `generateSiteMetadata(getSiteConfig(), ...)` ?
- [ ] `page.tsx` — renders `<StructuredData>`?
- [ ] `package.json` — has `upload:r2` script + `sharp` dep?
- [ ] `content/` — old site data cleaned?
- [ ] `public/images/` — old images cleaned?

## Phase 1: Create Skeleton

```bash
npx create-next-app@latest ssr-{slug} --typescript --tailwind --eslint --app --src-dir --import-alias "@/*" --turbopack
cd ssr-{slug}
npm install
```

## Phase 2: Copy Infrastructure (from golden template)

**Copy as-is:** `scripts/upload-to-r2.js`, `postcss.config.mjs`, `next.config.ts`

**13 shared components** (copy all then customize):
```
Breadcrumbs, CTAButton, FAQ, Features, Footer, Gallery,
GameIntro, Header, Hero, HomePage, ProsCons, ScrollReveal,
StructuredData, SystemReq + hooks/useScrollReveal.ts
```

**Lib files** (copy then customize): `types.ts`, `site.ts`, `seo.ts`

## Phase 3: Data Layer

Create `content/{slug}/data.ts` from Astro's `game.js`:

```ts
import type { GameData } from '@/lib/types'
export const data: GameData = { /* game.js content with type annotations */ }
```

## Phase 4: CSS

Copy `globals.css` from Astro, prepend `@import "tailwindcss";`

## Phase 5: Layout

Convert `BaseLayout.astro` → `layout.tsx`:
- Use `generateSiteMetadata(getSiteConfig(), ...)` for metadata
- Keep Google Fonts, favicon, theme-color meta
- CSS variables from `@theme` block as inline style on `<body>`

## Phase 6: Pages

Per `.astro` page → `page.tsx`:

| Astro | Next.js |
|-------|---------|
| `class=""` | `className=""` |
| `style="prop:val"` | `style={{ prop: 'val' }}` |
| `{game.field}` | `{data.field}` |
| frontmatter logic | component body |

## Phase 7: SEO Connection (⚠️ Most Missed)

- [ ] `layout.tsx` uses `generateSiteMetadata(getSiteConfig(), ...)`
- [ ] Home page renders `<StructuredData site={site} data={data} />`
- [ ] `data.ts` has complete `faqs` array (for FAQPage JSON-LD)

## Phase 8: Build & Verify

```bash
npm run build
# Check: 0 TS errors, all routes static, JSON-LD present
```

## Phase 9: Deploy

```bash
# Vercel + Cloudflare R2 setup
# Environment: ASSET_PREFIX, R2_* credentials
# package.json: add "upload:r2" script + sharp dependency
```

## Common Pitfalls

| Issue | Fix |
|-------|-----|
| Empty page content | Missing `<ScrollReveal />` on subpages |
| CSS variables broken | Mismatch between globals.css `@theme` and component usage |
| `components/` empty | Half-baked skeleton, copy all from golden template |
| No JSON-LD | `layout.tsx` hand-wrote metadata instead of using `generateSiteMetadata()` |
| Old images showing | `public/images/` has previous site's files |

## Acceptance Criteria

1. All pages render with correct content (visual match to Astro source)
2. Every page has unique title, OG image, and JSON-LD structured data
3. Build succeeds with 0 TypeScript errors
4. All routes are statically generated at build time
5. Fonts, CSS variables, and interactive elements work identically
