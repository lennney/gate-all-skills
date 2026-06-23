---
name: gate-ci
description: 🔄 CI/CD。加载 vercel-deploy，配 GitHub Actions 自动部署和 PR 预览。
---

Load `vercel-deploy` skill. Set up:

1. **Vercel Git Integration** → 连接 GitHub 仓库，main 分支自动部署
2. **Preview Deployments** → PR 自动生成预览链接
3. **CI 检查** → 确保 PR 通过 lint + typecheck
