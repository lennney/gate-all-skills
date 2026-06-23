---
name: gate-testcov
description: 🧪 测试覆盖。加载 e2e-playwright 和 ai-testing，让 AI 帮用户写测试。
---

Load `e2e-playwright` and `ai-testing`. Cover core paths first:

1. **核心 E2E 路径** → 首页加载 → 导航 → 表单提交 → CTA 跳转
2. **关键组件测试** → 渲染、交互、状态变化

用 `ai-testing` 生成测试代码。让用户确认后再提交。
