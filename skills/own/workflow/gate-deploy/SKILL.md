---
name: gate-deploy
description: 部署阶段。SEO 配好后加载。GitHub 推送 + Vercel 部署你在后台完成。
---

用户只需要知道结果。你来做：

1. `npm run build` 确保构建通过
2. 帮用户创建 GitHub 仓库并推送（问 GitHub 仓库名）
3. 引导用户在 Vercel 导入项目（需要用户操作 Vercel 页面）
4. 如需自定义域名，问用户域名是什么，告诉他在 DNS 加什么记录

部署完成后告诉用户网址，问要不要继续优化 → `/gate-optimize`
