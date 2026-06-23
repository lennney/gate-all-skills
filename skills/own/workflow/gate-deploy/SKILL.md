---
name: gate-deploy
description: 部署阶段。SEO 配好后加载。构建、推 GitHub、部署 Vercel、绑域名。
---

Guide the user through going live:

**1. 构建验证**
```bash
npm run build        # 0 错误才继续
```

**2. 推 GitHub**
```bash
git add . && git commit -m "feat: initial site"
gh repo create my-site --public --push
```

**3. Vercel 部署**
- 打开 vercel.com → Add New Project → 导入刚建的 GitHub 仓库
- 默认设置即可，Next.js 自动识别

**4. 绑域名** → Vercel 项目 Settings → Domains → 输入域名 → 按提示配 DNS

**5. 验证** → `curl https://你的域名` 返回 200

恭喜用户上线了 🎉 问他们要不要继续优化，引导去 `/gate-optimize`。
