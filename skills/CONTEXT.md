# CONTEXT.md — 领域术语表

## 技能（Skill）
一个 Claude Code 可执行的指令文件。包含 YAML frontmatter（name, description）和 markdown 正文。存放在 `skills/` 目录下的 `SKILL.md`。

## 用户调用（User-invoked）
仅通过 `/skill-name` 手动触发的技能。不适合 AI 自动触发。

## 模型调用（Model-invoked）
AI 可以根据上下文自动触发的技能。通过 frontmatter 中的 description 触发词匹配。

## Curated
从社区收集的第三方技能，存放在 `skills/curated/`。每个文件注明来源。

## Own
自建的专项技能，存放在 `skills/own/`。

## Seam
（来自 Michael Feathers）"可以在不修改某个位置的情况下改变行为的地方"。在 Next.js 中指 layout/loading/error 边界和组件接口。

## Deep Module
（来自《A Philosophy of Software Design》）接口小、实现多的模块。提供高 leverage（杠杆）给调用者。

## RSC / React Server Component
在服务端渲染的 React 组件，不发送 JavaScript 到客户端。Next.js App Router 的默认组件类型。

## Server Action
在服务端执行的异步函数，可以从客户端直接调用。Next.js 的 mutation 标准方案。

## ISR / Incremental Static Regeneration
静态页面增量更新策略。允许静态页面在部署后按需重新生成。

## Core Web Vitals
Google 定义的核心用户体验指标：LCP（加载性能）、INP（交互响应）、CLS（视觉稳定性）。