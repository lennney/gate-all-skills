---
name: gate-deploy
description: 部署阶段 — 构建、部署到 Vercel、绑定域名。SEO 配好之后再上线。
---

# Gate: 部署

网站做好了，上线。

## Step 1: 构建验证

```bash
npm run build
```

确保：
- [ ] 0 TypeScript 错误
- [ ] 构建成功
- [ ] 所有页面静态生成

## Step 2: 推送 GitHub

```bash
git add .
git commit -m "feat: initial site"
git remote add origin https://github.com/你的用户名/项目名.git
git push -u origin main
```

## Step 3: 部署到 Vercel

1. 打开 [vercel.com](https://vercel.com) → Add New Project
2. 导入 GitHub 仓库
3. 默认设置即可，Next.js 会自动识别
4. 点 Deploy

## Step 4: 绑定域名

1. Vercel 项目 → Domains → 输入你的域名
2. 按提示配置 DNS（Vercel 会给出 CNAME 记录）
3. 等 SSL 证书自动签发（几分钟）

## Step 5: 验证上线

```bash
curl https://你的域名.com
# 确认返回 HTML，不是 404
```

---

**上线了！** 🎉

**相关技能：** `vercel-deploy`
