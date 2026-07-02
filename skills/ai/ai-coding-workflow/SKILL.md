---
name: ai-coding-workflow
description: "AI 编码 / AI coding. 用户说"帮我写个组件"、"实现这个功能"、"写个 API 路由"时加载。先问清需求，在后台实现，完成后自动调 /ai-code-review 审查。"
trigger: 需要 AI 协助写代码
input: 代码需求
output: AI 生成的代码
next: ai-code-review
dependencies: 无
---

问用户："你要做什么？"

用户描述完，你：
1. 实现功能
2. 自己 diff 检查有没有问题（范围蔓延？重复？边界情况？）
3. 告诉用户改了哪些文件、改了什么

用户说"改这里" → 你改。3 轮迭代还不行 → revert 重来。
