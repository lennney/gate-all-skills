# gate-all-skills — AI 建站技能路由系统

> **用 AI 搭网站，从 0 到上线，一个命令搞定。**

---

## 🚀 快速开始

装完在你的 AI 编码助手里输入 `/gate`，它会带你走完建站全过程。

### 方法 1：skills.sh（推荐，支持 70+ 平台）

```bash
npx skills@latest add lennney/gate-all-skills
```

装完直接用，不用手动配置。

### 方法 2：git clone（Claude Code）

```bash
git clone https://github.com/lennney/gate-all-skills.git
ln -s "$(pwd)/gate-all-skills/skills" ~/.claude/skills
```

> `~/.claude/skills` 也可以用 `~/.agents/skills/`，看你用的工具。

### 多平台支持

| 平台 | 安装方式 |
|------|----------|
| **Claude Code** | `npx skills add lennney/gate-all-skills` |
| **Codex** | `npx skills add lennney/gate-all-skills` |
| **Cursor** | `npx skills add lennney/gate-all-skills` |
| **Windsurf** | `npx skills add lennney/gate-all-skills` |
| **GitHub Copilot** | `npx skills add lennney/gate-all-skills` |
| **Gemini CLI** | `npx skills add lennney/gate-all-skills` |
| 其他 60+ 平台 | `npx skills add lennney/gate-all-skills` |

---

## 🎯 核心特性

### 1. 智能路由系统

`/gate` 是总入口，根据你的需求自动路由到对应的技能：

```
/gate → 建站流程 / 设计 / 工程 / AI 辅助 / 产品 / 优化
```

### 2. 专业技能

覆盖建站全流程：
- **建站流程** (5个): 从需求讨论到优化
- **设计类** (11个): UI/UX、组件设计、样式系统
- **工程类** (6个): 代码审查、调试、测试
- **AI 类** (6个): AI 结对编程、代码审查、调试
- **产品类** (3个): PRD、验收标准、用户故事
- **优化类** (5个): 性能、无障碍、动效、测试、CI/CD
- **讨论类** (5个): 需求澄清、领域建模

### 3. 零配置使用

- **Background execution** — AI 做技术活，你只回答问题
- **Plain language** — AI 做完用大白话解释做了什么
- **Progressive** — 从 `/gate` 开始，自然深入到具体技能

---

## 📋 路由系统

### 🚀 建站流程

```
/gate → /gate-discuss → /gate-init → /gate-frontend → /gate-seo → /gate-optimize
```

| 阶段 | 技能 | 用途 |
|------|------|------|
| 1 | `/gate-discuss` | 需求讨论，明确要做什么 |
| 2 | `/gate-init` | 项目初始化，搭建脚手架 |
| 3 | `/gate-frontend` | 前端开发，组件+布局+样式 |
| 4 | `/gate-seo` | SEO 优化，让搜索引擎找到你 |
| 5 | `/gate-optimize` | 性能/无障碍/动效/测试优化 |

### 🎨 设计类

| 技能 | 用途 | 何时使用 |
|------|------|----------|
| `/ui-ux-pro-max` | 全栈 UI/UX 设计 | 需要完整的设计方案 |
| `/component-design` | 组件设计 | 设计可复用的组件 |
| `/styling-tailwind` | Tailwind CSS 实践 | 用 Tailwind 写样式 |
| `/ui-modernizer` | UI 升级 | 把旧界面变现代 |
| `/design-system` | 设计系统 | 建立统一的设计规范 |
| `/anti-ai-slop` | 反 AI 味设计 | 让设计更有人味 |

### 🔧 工程类

| 技能 | 用途 | 何时使用 |
|------|------|----------|
| `/code-review` | 代码审查 | 检查代码质量 |
| `/diagnosing-bugs` | 调试问题 | 遇到 bug 时 |
| `/tdd` | 测试驱动开发 | 先写测试再写代码 |
| `/prototype` | 快速原型 | 快速验证想法 |
| `/codebase-design` | 架构设计 | 设计代码结构 |

### 🤖 AI 辅助

| 技能 | 用途 | 何时使用 |
|------|------|----------|
| `/ai-coding-workflow` | AI 结对编程 | 让 AI 帮你写代码 |
| `/ai-code-review` | AI 代码审查 | 让 AI 检查代码 |
| `/ai-testing` | AI 测试生成 | 让 AI 写测试 |
| `/ai-debugging` | AI 调试 | 让 AI 帮你找 bug |
| `/ai-refactoring` | AI 重构 | 让 AI 优化代码 |

### 📋 产品类

| 技能 | 用途 | 何时使用 |
|------|------|----------|
| `/prd-development` | 写 PRD | 写产品需求文档 |
| `/acceptance-criteria` | 验收标准 | 定义功能完成标准 |
| `/user-story` | 用户故事 | 描述用户需求 |

### ⚡ 优化类

```
/gate-optimize → /gate-perf / /gate-a11y / /gate-animate / /gate-testcov / /gate-ci
```

| 技能 | 用途 | 何时使用 |
|------|------|----------|
| `/gate-perf` | 性能优化 | 网站加载太慢 |
| `/gate-a11y` | 无障碍优化 | 让所有人都能用 |
| `/gate-animate` | 动效优化 | 让网站更流畅 |
| `/gate-testcov` | 测试覆盖 | 加自动化测试 |

---

## 💡 使用技巧

### 1. 从 `/gate` 开始
不确定用什么技能？从 `/gate` 开始，系统会引导你。

### 2. 直接调用
知道自己要什么？直接调用具体技能，比如 `/ui-ux-pro-max`。

### 3. 组合使用
可以组合多个技能，比如：
- 先用 `/gate-discuss` 讨论需求
- 再用 `/ui-ux-pro-max` 做设计
- 最后用 `/gate-optimize` 优化

### 4. 随时切换
在一个技能中可以随时切换到其他技能，比如：
- 在 `/gate-frontend` 中发现需要设计 → 切换到 `/ui-ux-pro-max`
- 在 `/gate-optimize` 中发现需要调试 → 切换到 `/ai-debugging`

---

## 🎯 常见场景

### 场景 1：从零开始建站
```
/gate → /gate-discuss → /gate-init → /gate-frontend → /gate-seo → /gate-optimize
```

### 场景 2：优化现有网站
```
/gate → /gate-optimize → /gate-perf（或 /gate-a11y、/gate-animate）
```

### 场景 3：做 UI 设计
```
/ui-ux-pro-max → /component-design → /styling-tailwind
```

### 场景 4：写代码时需要帮助
```
/ai-coding-workflow → /ai-code-review → /ai-debugging
```

### 场景 5：产品规划
```
/prd-development → /acceptance-criteria → /user-story
```

---

## 🔄 更新

### 方法 1：skills.sh
```bash
npx skills update
```

### 方法 2：git clone 用户
```bash
cd gate-all-skills && git pull
```

就是这么简单。技能就是 Markdown 文件，更新 = 把新文件同步到本地。

---

## License

MIT — 随意使用。
