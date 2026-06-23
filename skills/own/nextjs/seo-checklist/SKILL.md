---
name: seo-checklist
description: SEO 完整检查清单。网站上线前后加载。按顺序检查每一项，确保搜索引擎能发现、理解、排名你的网站。
---

Run through this SEO checklist in order. Ask the user for each item, execute what you can.

## 1. 关键词
- 用户在搜索什么词来找这个网站？列出 5-10 个核心关键词
- 每个页面的目标关键词是什么？一页一词
- 用 Google 搜一下这些词，看竞争对手在做什么

## 2. 页面标题（最重要）
- 每页有唯一的 `<title>`，含核心关键词
- 格式：`主关键词 — 网站名` 或 `主关键词 | 网站名`
- 长度 50-60 字符，太长会被截断
- 首页标题要包含品牌名

## 3. Meta Description
- 每页有唯一的 `meta description`
- 120-155 字符
- 包含关键词 + 行动号召（"了解更多"、"立即下载"）
- 写成广告语——用户在搜索结果里看到会想点

## 4. 标题结构
- 每页只有一个 `<h1>`，含核心关键词
- `<h2>` 是主要章节，覆盖相关长尾词
- `<h3>` 是子章节
- 层级不能跳（h1 → h2 → h3，不能 h1 直接 h3）

## 5. 内容
- 每页至少 300 字正文（首页建议 600+）
- 自然地使用关键词，不要堆砌
- 用列表、表格、引用让内容易读
- 内部链接：相关页面之间互相链接

## 6. 图片
- 所有 `<img>` 有描述性的 `alt` 属性（含关键词机会）
- 图片文件名语义化：`fatekeeper-gameplay.jpg` 而非 `IMG_001.jpg`
- 懒加载：`loading="lazy"`（首屏以上不用）

## 7. 技术 SEO
- 加载 `seo-metadata` 技能配好 Metadata API
- Sitemap 包含所有公开页面
- Robots.txt 允许搜索引擎抓取
- canonical URL 每页正确
- 页面加载速度（Lighthouse > 90）
- 移动端适配（响应式）

## 8. Google Search Console
- 引导用户在 search.google.com/search-console 添加网站
- 验证网站所有权（Vercel 部署的话可以 DNS 验证）
- 提交 Sitemap URL
- 检查有没有抓取错误

## 9. 社交分享
- Open Graph 标签（Facebook/LinkedIn）：标题、描述、1200x630 图片
- Twitter Card：summary_large_image
- 预览：用 opengraph.xyz 测试分享效果

## 10. 验证上线
- `npm run build` 确认 Metadata 编译正确
- curl 或浏览器查看页面源码，确认 title/description/OG 都在
- 用 Google 搜索 `site:你的域名.com ` 检查有没有被收录（可能需要几天）

---

**原则：** SEO 不是一次性工作。上线后监控 Search Console，根据数据持续优化。
