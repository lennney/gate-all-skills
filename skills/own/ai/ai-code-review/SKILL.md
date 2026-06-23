---
name: ai-code-review
description: AI 代码审查。审查 PR 或代码变更时加载。按正确性→可维护性→性能→安全的顺序检查。
---

Review code changes in this order. Skip a level only if explicitly justified.

**1. 正确性** — 边界条件？null/空状态？类型安全？逻辑覆盖所有分支？
**2. 可维护性** — 重复代码？命名表意？复杂度可简化？
**3. 性能** — 不必要渲染？大 bundle？渲染路径中有昂贵计算？
**4. 安全** — 用户输入消毒？API 鉴权？密钥硬编码？

**输出格式：** 按严重程度列出问题（critical > major > minor）。critical 必须修，major 建议修，minor 可忽略。
