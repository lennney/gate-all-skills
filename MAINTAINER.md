# gate-all-skills — 维护指南

> 给仓库维护者看的文档。普通用户看 README 就够了。

---

## 更新技能

修改 `skills/` 目录下的 `SKILL.md` 文件后提交即可：

```bash
git add -A
git commit -m "update: xxx"
git push origin master
```

同事只需 `git pull` 就能同步。**不需要发版。**

> 技能就是 Markdown 文件。更新 = 把修改后的文件推上去。

---

## 发布 npm 包

只有改了 `bin/` 下的命令时才需要：

```bash
npm version patch   # 0.2.0 → 0.2.1
npm publish
```

---

## 技能编写规范

### frontmatter 字段

每个 `SKILL.md` 都要有：

| 字段 | 必填 | 说明 |
|------|------|------|
| `name` | ✅ | 唯一标识，用 kebab-case |
| `description` | ✅ | 中文为主，写全用户可能的触发词 |
| `trigger` | ✅ | 什么情况会触发这个技能 |
| `input` | ✅ | 技能需要什么输入 |
| `output` | ✅ | 技能产出什么 |
| `dependencies` | ❌ | 依赖的技能列表 |

### 路径引用

用 skill name，不用路径：

```
正确：跳到 /ai-debugging
错误：跳到 skills/ai/ai-debugging/SKILL.md
```

### description 写法

把用户可能说的词都列上，例如：

```yaml
# 好
description: "AI 调试 / AI debugging. 用户说"帮我 debug"、"报错了"、"这个 bug 怎么修"、"抛异常了"时加载。让用户描述问题，你在后台分析根因并修复。"

# 不好
description: "AI 调试技能"
```

### 讨论类技能

加上 `disable-model-invocation: true`，避免 AI 自己调用。

### 中文优先

团队用中文，description 和内容以中文为主。

---

## 目录结构

```
skills/
├── website/       (11)  建站：组件、布局、样式、SEO
├── discussion/    (5)   探讨：需求澄清、领域建模
├── engineering/   (6)   工程：TDD、调试、代码审查
├── design/        (11)  设计：UI/UX、设计系统
├── product/       (3)   产品：PRD、验收标准、用户故事
├── ai/            (6)   AI 辅助：编码/审查/测试/调试/重构/Git
└── workflow/      (10)  路由系统 —— 入口 `/gate`
```

每个技能 = 一个目录下的 `SKILL.md` 文件。目录名和 `name` 字段保持一致。

### 新增一个技能

```bash
mkdir skills/<category>/<skill-name>
cat > skills/<category>/<skill-name>/SKILL.md << 'EOF'
---
name: <skill-name>
description: "<中文描述 / English description. 用户说什么话会触发这个技能>"
trigger: <什么情况加载>
input: <需要什么输入>
output: <产出什么>
---
<技能内容>
EOF
```

然后在 `plugin.json` 里注册：

```json
{
  "name": "<skill-name>",
  "description": "和 SKILL.md 的 description 一致",
  "path": "<category>/<skill-name>/SKILL.md"
}
```

---

## 路由系统维护

`/gate` 是总入口，它会根据上下文自动路由到子技能。

路由逻辑在 `skills/workflow/gate/SKILL.md` 中定义。

### 新增路由

在 `gate/SKILL.md` 的 frontmatter 中添加新的条件和对应的子技能即可。不用改其他文件。

### 路由原则

- `/gate` 只做路由分发，不做具体工作
- 子技能只关注自己的领域
- 每个技能的完整路由信息在其自身的 `SKILL.md` 的 frontmatter 中

---

## 发布流程

1. 改完技能 → `git push`
2. 同事 `git pull` 同步
3. 如果改了 CLI 命令 → `npm version patch && npm publish`

---

## 相关资料

- [Matt Pocock's skills](https://github.com/mattpocock/skills) — 实践参考
- [skills.sh](https://skills.sh) — 多平台分发工具
