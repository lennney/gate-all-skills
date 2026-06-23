---
name: gate-seo
description: SEO 阶段。前端开发完成后加载。先检查 Metadata 技术配置，再跑 SEO 完整清单。
---

Set up SEO for the site. Two steps:

**1. 技术 SEO** — 加载 `seo-metadata` 配好 Metadata API、Sitemap、Robots
**2. 完整检查** — 加载 `seo-checklist` 逐个检查关键词、标题、内容、图片、GSC

**验证：** `npm run build` → 检查输出 HTML 有 title + description + OG 标签

完成后引导用户去 `/gate-deploy`。
