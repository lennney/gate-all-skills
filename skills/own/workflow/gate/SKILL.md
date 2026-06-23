---
name: gate
description: 建站工作流路由 — 从 0 到 1 搭建网站的每个阶段。输入你当前在做的事，自动路由到对应技能和指南。
---

# Gate — 建站工作流路由

从 0 到 1 搭建网站，按阶段推进。每个阶段有对应的技能和步骤。

## 你在哪个阶段？

### 🗣️ 探讨阶段
> `/gate-discuss`

还不知道要做成什么样？先聊清楚需求、用户、功能、技术选型。

**路由到：** `grill-me` · `domain-modeling` · `handoff`

### 🚀 初始化
> `/gate-init`

项目定型了，开始搭脚手架。

**路由到：** `project-init`

### 🎨 前端开发
> `/gate-frontend`

写组件、搭布局、上样式、接数据。

**路由到：** `component-design` · `layouts-routing` · `styling-tailwind` · `data-fetching` · `accessibility` · `error-handling` · `performance` · `e2e-playwright`

### 🔍 SEO
> `/gate-seo`

让搜索引擎找到你的网站。

**路由到：** `seo-metadata`

### 🚢 部署
> `/gate-deploy`

上线、域名、持续部署。

**路由到：** `vercel-deploy`

### 🤖 AI 辅助（贯穿全程）
> `/gate-ai`

任何阶段你都需要 AI 帮忙。

**路由到：** `ai-coding-workflow` · `ai-code-review` · `ai-testing` · `ai-debugging` · `ai-refactoring` · `ai-git-workflow`

---

## 快速指南

```
同事: "我想搭一个游戏介绍网站"
你:   /gate-discuss  → 聊清楚需求
       /gate-init     → 建项目
       /gate-frontend → 写页面
       /gate-seo      → 配 SEO
       /gate-deploy   → 上线

卡住了随时 /gate-ai 找 AI 帮忙
```
