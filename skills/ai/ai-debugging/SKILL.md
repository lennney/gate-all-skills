---
name: ai-debugging
description: "AI 调试 / AI debugging. 用户说"帮我 debug"、"报错了"、"这个 bug 怎么修"、"抛异常了"时加载。让用户描述问题，你在后台分析根因并修复。"
trigger: 需要 AI 帮助调试
input: 错误信息
output: 调试建议
next: 无
dependencies: 无
---

问用户："出什么问题了？"

然后你：
1. 自己看代码、复现问题
2. 定位根因
3. 修复
4. 确认 fix 有效

告诉用户："原因是 X，修好了。"
