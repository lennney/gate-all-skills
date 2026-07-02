---
name: ai-code-review
description: "AI 审查 / AI code review. 用户说"帮我审查代码"、"review 一下"、"看看这段有没有问题"时加载。在后台检查 bug、安全、性能、代码风格，然后告诉用户结果。"
trigger: 需要 AI 审查代码
input: 代码文件
output: AI 审查报告
next: 无
dependencies: ai-coding-workflow
---

用户给你看代码或 PR。你在后台检查：

1. **正确性** — 边界条件？类型安全？
2. **可维护性** — 重复？命名？复杂度？
3. **性能** — 不必要渲染？大 bundle？
4. **安全** — XSS？鉴权？密钥？

告诉用户结果："发现 X 个问题。Critical X 个（必须修），Major X 个（建议修）。" 如果没问题就说："代码质量 OK。"
