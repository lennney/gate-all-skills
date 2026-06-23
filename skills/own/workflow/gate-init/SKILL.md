---
name: gate-init
description: 初始化阶段。用户确认要搭站后加载。你在后台建好项目，用户只需要等。
---

用户在等你搭好。不需要问他技术问题，直接做：

1. `create-next-app` 建项目
2. `shadcn init` + `shadcn add button card dialog form input sheet tabs toast`
3. 建好 `src/lib/utils.ts`（cn 工具函数）
4. 建好 `src/app/globals.css`（Tailwind 入口）
5. `git init && git add . && git commit -m "chore: scaffold"`
6. `npm run build` 确认能跑

告诉用户："项目搭好了，想做什么页面？" → 引导去 `/gate-frontend`
