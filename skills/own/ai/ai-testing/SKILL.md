---
name: ai-testing
description: AI 测试生成。用户需要写测试时加载。让用户描述要测什么 → AI 生成 → 用户审查 → 运行验证。
---

Generate tests by asking the user what to test. One component/function at a time.

**For each test target, ask:**
- 输入是什么？期望输出是什么？
- 有哪些边界情况？（空值、异常、极限值）
- 需要测 loading/error/empty 状态吗？

**Generated test template:**
```tsx
describe("Component", () => {
  it("renders correctly", () => { /* ... */ })
  it("handles empty state", () => { /* ... */ })
  it("responds to user interaction", async () => { /* ... */ })
})
```

**验证：** `npm test` 跑通后再提交。测试行为（输出），不测试实现（内部方法）。
