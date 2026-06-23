---
name: ai-git-workflow
description: AI Git 操作。用户需要 commit/PR/merge 帮助时加载。让 AI 写 message、PR 描述、解决冲突。
---

Help with git operations:

**Commit message：** 用 conventional commits 格式。`feat:` `fix:` `refactor:` `chore:` `docs:`
**PR 描述：** What（改了啥）+ Why（为什么改）+ Testing（怎么验证）
**冲突解决：** 分析两边改动意图，合并不丢失任何一方的变更
**Changelog：** `git log --oneline v1.0.0..HEAD` → 分组为 Features / Bug Fixes / Chores
**预审查：** 提交前让 AI 检查 diff 有无 console.log、调试代码、密钥泄露
