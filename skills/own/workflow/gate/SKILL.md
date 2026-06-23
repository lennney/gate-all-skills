---
name: gate
description: 建站工作流路由。同事说想搭网站、优化网站、或需要 AI 帮助时加载。问清楚他在哪个阶段，然后路由到对应 gate-* 技能。
---

Ask the user what they want to do, then route them:

**🆕 从零搭建（未开始）**
→ `/gate-discuss` — 先聊清楚需求、功能、技术选型
→ `/gate-init` — 搭项目脚手架
→ `/gate-frontend` — 前端开发
→ `/gate-seo` — 配置 SEO
→ `/gate-deploy` — 部署上线

**📈 已有网站想优化**
→ `/gate-optimize` — 选优化方向

**🤖 需要 AI 帮忙**
→ `/gate-ai` — 选场景（写代码/审查/测试/调试/重构/Git）

引导用户按顺序走，完成一个阶段再进下一个。
