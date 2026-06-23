---
name: gate-init
description: 初始化阶段 — 搭项目脚手架、装依赖、建目录结构。使用前必须先明确需求（/gate-discuss）。
---

# Gate: 初始化

项目定型了，开始搭架子。

## Step 1: 创建项目

```bash
npx create-next-app@latest my-site --typescript --tailwind --eslint --app --src-dir --import-alias "@/*"
cd my-site
```

参数说明：
- `--typescript`：TypeScript 标配
- `--tailwind`：Tailwind v4
- `--app`：App Router
- `--src-dir`：代码放 `src/` 下，干净

## Step 2: 装 UI 组件库

```bash
npx shadcn@latest init -d
npx shadcn@latest add button card dialog dropdown-menu form input sheet tabs toast
```

## Step 3: 建目录结构

```
src/
├── app/
│   ├── layout.tsx          ← 根布局（字体、SEO metadata）
│   ├── page.tsx            ← 首页
│   ├── globals.css         ← 全局样式 + Tailwind
│   ├── sitemap.ts          ← Sitemap
│   └── robots.ts           ← Robots.txt
├── components/
│   └── ui/                 ← shadcn/ui 组件
├── lib/
│   ├── utils.ts            ← cn() 工具函数
│   └── constants.ts        ← 站点配置常量
└── public/
    └── images/             ← 图片资源
```

## Step 4: 初始化 Git

```bash
git init
git add .
git commit -m "chore: scaffold Next.js project"
```

## Step 5: 验证能跑

```bash
npm run dev   # 打开 http://localhost:3000
npm run build # 确认构建成功
```

---

**脚手架好了？** → `/gate-frontend` 开始开发

**相关技能：** `project-init`
