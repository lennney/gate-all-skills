---
name: gate-seo
description: SEO 阶段。前端完成后加载。问 2 个问题，后台配好所有 SEO。
---

用户不需要懂 SEO。问 2 个问题：

1. "网站一句话介绍是什么？" → 用作 description
2. "目标关键词有哪些？" → 列出 3-5 个

然后你在后台：
1. 配好 `layout.tsx` 的 metadata（title template + description + OG）
2. 每个已有页面加 `generateMetadata`
3. 创建 `sitemap.ts`
4. 创建 `robots.ts`
5. `npm run build` 验证 OG 标签正确

告诉用户："SEO 配好了，可以上线了" → `/gate-deploy`
