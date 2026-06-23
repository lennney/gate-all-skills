---
name: ai-coding-workflow
description: AI 结对编程循环。开始新任务时加载。让用户写任务描述 → AI 生成 → 审查差异 → 迭代修复。
---

Guide the user through this loop for each coding task:

1. **用户写任务描述** → 包含：文件路径、约束、非目标。不够具体就追问
2. **AI 生成代码** → 实现功能
3. **审查 diff** → `git diff --stat` 看改了哪些文件，检查：范围蔓延？重复？过度设计？遗漏边界？
4. **迭代** → 最多 3 轮，用户提具体 fix 要求
5. **提交** → 用户确认后 `git add -p` 选择性提交

如果 AI 在同一个问题兜圈子超过 3 轮：revert 所有改动，重写任务描述，重新开始。
