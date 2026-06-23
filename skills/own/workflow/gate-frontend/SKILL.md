---
name: gate-frontend
description: 前端开发阶段 — 写组件、搭布局、上样式、接数据。从首页开始，一页一页推进。
---

# Gate: 前端开发

项目搭好了，开始写页面。从首页开始，一页一页来。

## 工作方式

每个页面按这个循环推进：

```
1. 搭布局  →  页面结构、路由
2. 写组件  →   首页/页面的各个功能区块
3. 上样式  →  Tailwind 美化
4. 接数据  →  内容数据（文案、图片）
5. 预览    →  npm run dev 看效果
```

## 从首页开始

首页（`src/app/page.tsx`）是最重要的页面，通常包含：

```
Hero        → 大标题 + 描述 + CTA 按钮
Features    → 核心功能/卖点
Content     → 正文/介绍
CTA         → "马上开始" 引导
Footer      → 版权 + 链接
```

## 常用操作

### 搭布局
> "创建 `/about` 页面，用 route group 组织营销页和功能页"

**相关技能：** `layouts-routing`

### 写组件
> "创建一个 ProductCard 组件，接收 title/description/image 作为 props"

**相关技能：** `component-design` · `data-fetching`

### 上样式
> "用 Tailwind 实现响应式卡片网格，mobile 1 列，desktop 3 列"

**相关技能：** `styling-tailwind`

### 异常处理
> "API 请求失败时显示错误提示，网络慢时显示 loading"

**相关技能：** `error-handling` · `accessibility` · `performance`

---

**页面写好了？** → `/gate-seo` 配搜索引擎

**卡住了？** → `/gate-ai` 找 AI 帮忙
