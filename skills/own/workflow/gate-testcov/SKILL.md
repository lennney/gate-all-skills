---
name: gate-testcov
description: 测试覆盖。用户要加测试时加载。你在后台给核心功能写 E2E 测试，让用户确认。
---

自动做：

1. 分析网站核心路径（首页→导航→CTA）
2. 用 Playwright 写 E2E 测试覆盖这些路径
3. `npx playwright test` 跑通
4. 告诉用户写了哪些测试

用户只需要知道测试覆盖了哪些功能，全部通过了。
