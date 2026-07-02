---
name: ai-git-workflow
description: "AI Git 操作 / AI git workflow. 用户说"帮我 commit"、"提个 PR"、"push 一下"、"git 操作"时加载。在后台生成 commit message / PR 描述，用户确认后执行。"
trigger: 需要处理 Git 操作
input: 代码变更
output: commit/PR 描述
next: 无
dependencies: 无
---

帮用户处理 Git 操作：

**Commit：** `git diff --cached` 看完自动写 message，给用户确认
**PR：** 基于 `git log main..HEAD` 生成描述
**冲突：** 分析两边改动意图，合并后让用户验证
