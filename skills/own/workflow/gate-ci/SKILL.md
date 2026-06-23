---
name: gate-ci
description: CI/CD。用户要自动部署时加载。你在后台配置好 GitHub Actions + Vercel 集成。
---

配置自动部署：

1. GitHub 仓库连接 Vercel（引导用户去 Vercel 点一下 Import）
2. main 分支推送自动部署到生产
3. PR 自动生成 preview URL

告诉用户："以后推 main 分支就会自动上线了，PR 会有预览链接。"
