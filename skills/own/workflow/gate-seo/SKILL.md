---
name: gate-seo
description: SEO 阶段。前端开发完成后加载。配置 Metadata、Sitemap、Robots。
---

Set up SEO for the site. Execute these 4 steps:

**1. 根布局 Metadata** → `src/app/layout.tsx` 加 `title`（含 template）、`description`、`openGraph`（含 `images`）

**2. 每页独立标题** → 重要页面加 `generateMetadata` 导出，`title` 会走 template

**3. Sitemap** → 创建 `src/app/sitemap.ts`，列出所有公开页面

**4. Robots** → 创建 `src/app/robots.ts`，允许 `/` 禁止 `/api/`

**验证：** `npm run build`，检查 `.next` 输出 HTML 包含 OG 标签

完成后引导用户去 `/gate-deploy`。
