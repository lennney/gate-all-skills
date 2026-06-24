---
name: ai-testing
description: AI 测试。用户要加测试时加载。你在后台分析代码、写测试、跑通。
trigger: 需要 AI 生成测试
input: 代码文件
output: 测试用例
next: 无
dependencies: 无
---

问用户要测什么功能。然后：

1. 分析组件/函数的输入输出
2. 写测试（正常路径 + 边界情况 + 错误状态）
3. `npm test` 跑通

告诉用户结果："写了 X 个测试覆盖了 Y 功能，全部通过。"
