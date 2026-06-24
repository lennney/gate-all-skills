# Skills 路由系统 AI 使用指南

## 🎯 概述

这是一个给 AI 使用的技能路由系统，帮助 AI 根据用户需求自动选择和调用合适的技能。

---

## 📋 路由决策流程

### 1. 分析用户意图

从用户输入中提取关键词，匹配意图类型：

| 意图类型 | 关键词 | 路由目标 |
|----------|--------|----------|
| 建站 | 搭建、新建、从零开始 | `/gate-discuss` |
| 前端开发 | 页面、组件、样式、UI | `/gate-frontend` |
| SEO | 搜索引擎、SEO、优化 | `/gate-seo` |
| 部署 | 上线、部署、发布 | `/gate-deploy` |
| UI 设计 | 设计、界面、原型、UX | `/ui-ux-pro-max` |
| 组件设计 | 组件、复用、组件库 | `/component-design` |
| 样式 | Tailwind、CSS、样式 | `/styling-tailwind` |
| 代码审查 | 审查、review、检查代码 | `/code-review` |
| 调试 | bug、调试、问题、错误 | `/diagnosing-bugs` |
| 测试 | 测试、TDD、单元测试 | `/tdd` |
| 重构 | 重构、优化代码、代码结构 | `/ai-refactoring` |
| 产品 | PRD、需求、用户故事 | `/prd-development` |
| 优化 | 优化、性能、速度 | `/gate-optimize` |

### 2. 检查项目状态

```bash
# 检查是否存在项目
ls package.json 2>/dev/null    # Node.js 项目
ls pyproject.toml 2>/dev/null  # Python 项目

# 检查是否有 Git 仓库
git status 2>/dev/null

# 检查是否有部署配置
ls vercel.json 2>/dev/null     # Vercel 部署
```

**状态判断**：
- 无项目 → 新建项目流程
- 有项目但未完成 → 继续开发流程
- 项目完成但未部署 → 部署流程
- 项目已部署 → 优化流程

### 3. 选择技能

根据意图和项目状态，选择最匹配的技能。

---

## 🚀 建站流程（0→1）

```yaml
gate-discuss:
  trigger: 用户想搭建新网站，但不确定具体需求
  input: 用户的模糊想法
  output: 明确的需求文档
  next: gate-init
  dependencies: 无

gate-init:
  trigger: 需求已明确，需要初始化项目
  input: 需求文档
  output: 项目脚手架
  next: gate-frontend
  dependencies: gate-discuss

gate-frontend:
  trigger: 项目已初始化，需要开发前端
  input: 项目脚手架
  output: 前端页面和组件
  next: gate-seo
  dependencies: gate-init

gate-seo:
  trigger: 前端开发完成，需要优化 SEO
  input: 前端代码
  output: SEO 优化后的代码
  next: gate-deploy
  dependencies: gate-frontend

gate-deploy:
  trigger: SEO 优化完成，需要部署上线
  input: 优化后的代码
  output: 已部署的网站
  next: gate-optimize
  dependencies: gate-seo
```

---

## ⚡ 优化流程（1→2→3）

```yaml
gate-optimize:
  trigger: 网站已上线，需要优化
  input: 已部署的网站
  output: 优化建议
  next: gate-perf / gate-a11y / gate-animate
  dependencies: gate-deploy

gate-perf:
  trigger: 网站加载速度慢
  input: 性能数据
  output: 性能优化方案
  next: 无
  dependencies: gate-optimize

gate-a11y:
  trigger: 需要提升网站可访问性
  input: 可访问性审计报告
  output: 可访问性优化方案
  next: 无
  dependencies: gate-optimize

gate-animate:
  trigger: 需要添加动效
  input: 动效需求
  output: 动效实现
  next: 无
  dependencies: gate-optimize
```

---

## 🎨 设计类

```yaml
ui-ux-pro-max:
  trigger: 需要完整的 UI/UX 设计方案
  input: 需求文档或截图
  output: 设计稿和规范
  next: component-design / styling-tailwind
  dependencies: 无

component-design:
  trigger: 需要设计可复用的组件
  input: 设计稿或需求
  output: 组件设计文档
  next: styling-tailwind
  dependencies: ui-ux-pro-max

styling-tailwind:
  trigger: 需要用 Tailwind CSS 写样式
  input: 组件结构
  output: 样式代码
  next: 无
  dependencies: component-design

ui-modernizer:
  trigger: 需要升级旧界面
  input: 旧界面截图或代码
  output: 现代化设计
  next: component-design
  dependencies: 无

design-system:
  trigger: 需要建立设计系统
  input: 设计规范
  output: 设计系统文档
  next: component-design
  dependencies: 无

anti-ai-slop:
  trigger: 设计看起来太 AI 生成，需要更人性化
  input: AI 生成的设计
  output: 更人性化的设计
  next: 无
  dependencies: 无
```

---

## 🔧 工程类

```yaml
code-review:
  trigger: 需要审查代码质量
  input: 代码文件
  output: 审查报告
  next: diagnosing-bugs / ai-refactoring
  dependencies: 无

diagnosing-bugs:
  trigger: 遇到 bug 需要调试
  input: 错误信息或异常行为
  output: bug 原因和修复方案
  next: 无
  dependencies: 无

tdd:
  trigger: 需要用测试驱动开发
  input: 功能需求
  output: 测试用例和实现代码
  next: 无
  dependencies: 无

prototype:
  trigger: 需要快速验证想法
  input: 想法描述
  output: 可交互原型
  next: ui-ux-pro-max
  dependencies: 无

codebase-design:
  trigger: 需要设计代码架构
  input: 项目需求
  output: 架构设计文档
  next: 无
  dependencies: 无
```

---

## 🤖 AI 辅助类

```yaml
ai-coding-workflow:
  trigger: 需要 AI 协助写代码
  input: 代码需求
  output: AI 生成的代码
  next: ai-code-review
  dependencies: 无

ai-code-review:
  trigger: 需要 AI 审查代码
  input: 代码文件
  output: AI 审查报告
  next: 无
  dependencies: ai-coding-workflow

ai-testing:
  trigger: 需要 AI 生成测试
  input: 代码文件
  output: 测试用例
  next: 无
  dependencies: 无

ai-debugging:
  trigger: 需要 AI 帮助调试
  input: 错误信息
  output: 调试建议
  next: 无
  dependencies: 无

ai-refactoring:
  trigger: 需要 AI 帮助重构
  input: 代码文件
  output: 重构建议
  next: code-review
  dependencies: 无
```

---

## 📋 产品类

```yaml
prd-development:
  trigger: 需要写产品需求文档
  input: 产品想法
  output: PRD 文档
  next: acceptance-criteria
  dependencies: 无

acceptance-criteria:
  trigger: 需要定义功能完成标准
  input: PRD 文档
  output: 验收标准列表
  next: user-story
  dependencies: prd-development

user-story:
  trigger: 需要描述用户需求
  input: 验收标准
  output: 用户故事列表
  next: 无
  dependencies: acceptance-criteria
```

---

## 💬 讨论类

```yaml
gate-discuss:
  trigger: 不确定要做什么，需要讨论
  input: 模糊的想法
  output: 明确的需求
  next: gate-init
  dependencies: 无

domain-modeling:
  trigger: 需要设计业务模型
  input: 业务需求
  output: 领域模型
  next: codebase-design
  dependencies: 无

handoff:
  trigger: 需要交接上下文
  input: 当前进度
  output: 上下文文档
  next: 无
  dependencies: 无
```

---

## 🎯 使用示例

### 示例 1：新用户想建站
```
用户：我想搭建一个个人网站
AI：分析意图 → 建站
AI：检查项目状态 → 无项目
AI：路由到 → /gate-discuss
AI：执行 → 需求讨论
AI：输出 → 明确的需求文档
AI：推荐下一步 → /gate-init
```

### 示例 2：用户有项目需要优化
```
用户：我的网站加载太慢了
AI：分析意图 → 性能优化
AI：检查项目状态 → 项目已部署
AI：路由到 → /gate-perf
AI：执行 → 性能优化
AI：输出 → 性能优化方案
```

### 示例 3：用户需要设计帮助
```
用户：我想设计一个登录页面
AI：分析意图 → UI 设计
AI：检查项目状态 → 有项目
AI：路由到 → /ui-ux-pro-max
AI：执行 → UI/UX 设计
AI：输出 → 设计稿和规范
AI：推荐下一步 → /component-design
```

---

## ⚠️ 注意事项

1. **优先使用 gate-* 技能**：建站流程和优化流程优先使用对应的 gate 技能
2. **直接调用技能**：设计、工程、AI、产品类技能可以直接调用
3. **检查依赖**：调用技能前检查是否有依赖技能
4. **更新状态**：完成技能后更新项目状态
5. **推荐下一步**：完成后推荐下一个相关技能

---

## 📚 更多资源

- [技能清单](./README.md) - 所有技能列表
- [变更日志](./CHANGELOG.md) - 版本更新历史
- [路由优化建议](./ROUTING-OPTIMIZATION.md) - 优化建议
