---
name: gate-seo
description: SEO 阶段 — 让搜索引擎能找到你的网站。配 Metadata、结构化数据、Sitemap。在部署前做。
---

# Gate: SEO

页面写好了，让搜索引擎能找到它。

## 必做 4 件事

### 1. 根布局 Metadata

```ts
// src/app/layout.tsx
export const metadata: Metadata = {
  title: { default: "网站名称", template: "%s | 网站名称" },
  description: "一句话描述这个网站",
  openGraph: {
    title: "网站名称",
    description: "一句话描述",
    images: [{ url: "/og-image.png", width: 1200, height: 630 }],
  },
}
```

### 2. 每个页面独立标题

```ts
// src/app/about/page.tsx
export const metadata: Metadata = {
  title: "关于我们",       // → 渲染为 "关于我们 | 网站名称"
  description: "了解我们的故事",
}
```

### 3. Sitemap

```ts
// src/app/sitemap.ts
export default function sitemap() {
  return [
    { url: "https://example.com", priority: 1 },
    { url: "https://example.com/about", priority: 0.8 },
  ]
}
```

### 4. Robots.txt

```ts
// src/app/robots.ts
export default function robots() {
  return {
    rules: { userAgent: "*", allow: "/", disallow: "/api/" },
    sitemap: "https://example.com/sitemap.xml",
  }
}
```

## 验证

```bash
npm run build
# 然后检查 .next 目录的 HTML 里有 OG 标签和 JSON-LD
```

---

**SEO 完事了？** → `/gate-deploy` 上线

**相关技能：** `seo-metadata`
