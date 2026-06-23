---
name: gate-init
description: 初始化阶段。需求明确后加载。搭 Next.js 项目脚手架。
---

Run these steps in order. Execute commands when possible, show them when not.

**1. 创建项目**
```bash
npx create-next-app@latest my-site --typescript --tailwind --eslint --app --src-dir --import-alias "@/*"
cd my-site
```

**2. 安装 UI 库**
```bash
npx shadcn@latest init -d
npx shadcn@latest add button card dialog form input sheet tabs toast
```

**3. 建目录结构**
```
src/
├── app/             layout.tsx + page.tsx + globals.css
├── components/ui/   shadcn 组件
├── lib/             utils.ts + constants.ts
└── public/images/   图片
```

**4. Git init + build 验证**
```bash
git init && git add . && git commit -m "chore: scaffold"
npm run build        # 确认构建成功
```

完成后引导用户去 `/gate-frontend`。
