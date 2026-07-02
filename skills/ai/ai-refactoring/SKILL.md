---
name: ai-refactoring
description: "AI 重构 / AI refactoring. 用户说"重构这段代码"、"优化代码结构"、"把这块抽出来"时加载。先让用户定范围，你在后台改完自动验证。建议先跑 /tdd 保证测试覆盖。"
trigger: 需要 AI 帮助重构
input: 代码文件
output: 重构建议
next: code-review
dependencies: 无
---

问用户要重构什么。然后：

1. 改之前跑 `npm run typecheck && npm test && npm run build` 记下 baseline
2. 执行重构
3. 再跑一遍验证通过
4. 告诉用户改了哪些

用户只需要知道结果，不需要参与过程。
