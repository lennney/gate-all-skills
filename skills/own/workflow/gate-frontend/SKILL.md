---
name: gate-frontend
description: 前端开发阶段。脚手架搭好后加载。一页一页推进，每页按布局→组件→样式→数据的顺序。
---

Guide the user through building pages one at a time. Start from the home page.

**For each page, follow this loop:**

1. **布局** → 问用户页面结构，用 `layouts-routing` 技能搭路由
2. **组件** → 拆页面为组件，用 `component-design` 设计接口
3. **样式** → Tailwind 美化，用 `styling-tailwind` 技能
4. **数据** → 接内容文案和图片
5. **预览** → `npm run dev` 让用户看效果

**首页常见结构：** Hero → Features → Content → CTA → Footer

每个页面完成后让用户确认再继续下一页。全部做完引导去 `/gate-seo`。

需要时加载子技能：`layouts-routing` · `component-design` · `styling-tailwind` · `data-fetching` · `error-handling`
