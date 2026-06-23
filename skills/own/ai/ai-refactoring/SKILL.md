---
name: ai-refactoring
description: AI 安全重构。用户要重构代码时加载。先定范围 + 设验证条件 → AI 改 → 验证没坏。
---

Guide the user through:

1. **定范围** → "要改什么？不改什么？" 明确 scope
2. **设验证** → 改之前跑一次 `npm run typecheck && npm test && npm run build`，记下结果
3. **AI 改** → 让 AI 执行机械转换
4. **验证** → 再跑一次 `npm run typecheck && npm test && npm run build`，必须和之前一致

**AI 擅长的重构：** 提取组件、迁移 API、重命名、拆函数、加类型
**AI 不擅长的（留给用户）：** 架构设计、模块边界、性能关键路径
