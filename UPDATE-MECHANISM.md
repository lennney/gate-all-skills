# Skills 更新机制优化

> 基于 Claude Code Skills 最佳实践，2026-06-24

---

## 📋 当前更新机制

### 现状
```bash
# 安装技能
npx skills@latest add lennney/skills

# 更新技能（需要重新执行）
npx skills@latest add lennney/skills
```

### 问题
1. **手动更新**：用户需要手动执行命令
2. **无版本控制**：没有明确的版本管理
3. **无自动更新**：不会自动检查更新
4. **覆盖风险**：重新安装可能覆盖用户自定义

---

## 🎯 优化方案

### 方案 1：Git Submodule（推荐）

**原理**：将 skills 仓库作为 Git Submodule 添加到项目中

**优点**：
- 版本控制：可以锁定特定版本
- 自动同步：`git submodule update --remote`
- 易于管理：Git 原生支持

**实现步骤**：
```bash
# 1. 添加 skills 作为 submodule
git submodule add https://github.com/lennney/skills.git .claude/skills

# 2. 更新到最新版本
cd .claude/skills
git pull origin main
cd ../..
git add .claude/skills
git commit -m "chore: update skills"

# 3. 其他用户克隆后初始化
git submodule init
git submodule update
```

**目录结构**：
```
project/
├── .claude/
│   └── skills/          # Git submodule
│       ├── gate/
│       ├── ui-ux-pro-max/
│       └── ...
├── src/
└── package.json
```

### 方案 2：npm 包管理

**原理**：将 skills 发布为 npm 包

**优点**：
- 版本管理：npm 语义化版本
- 自动更新：`npm update`
- 依赖管理：可以声明依赖

**实现步骤**：
```json
// package.json
{
  "dependencies": {
    "@lennney/skills": "^1.0.0"
  }
}
```

```bash
# 安装
npm install @lennney/skills

# 更新
npm update @lennney/skills
```

**目录结构**：
```
project/
├── node_modules/
│   └── @lennney/
│       └── skills/
│           ├── gate/
│           ├── ui-ux-pro-max/
│           └── ...
├── .claude/
│   └── skills/ -> ../node_modules/@lennney/skills  # 符号链接
└── package.json
```

### 方案 3：CLI 工具增强

**原理**：增强 `skills` CLI 工具，支持更新和版本管理

**功能**：
```bash
# 检查更新
skills check-update

# 更新所有技能
skills update

# 更新特定技能
skills update gate

# 锁定版本
skills lock 1.0.0

# 解锁版本
skills unlock
```

**配置文件**：
```json
// .skills.json
{
  "registry": "https://github.com/lennney/skills",
  "version": "1.0.0",
  "locked": false,
  "installed": {
    "gate": "1.0.0",
    "ui-ux-pro-max": "1.0.0",
    "component-design": "1.0.0"
  }
}
```

### 方案 4：自动同步服务

**原理**：创建一个服务，自动同步技能更新

**架构**：
```
GitHub Repository (lennney/skills)
    ↓ (webhook)
Sync Service
    ↓ (git pull)
User's Project
```

**实现**：
1. 在 GitHub 仓库配置 webhook
2. 当有新提交时，触发同步服务
3. 同步服务自动更新用户项目中的技能

---

## 📊 方案对比

| 方案 | 优点 | 缺点 | 适用场景 |
|------|------|------|----------|
| Git Submodule | 版本控制、易管理 | 需要 Git 知识 | 团队协作项目 |
| npm 包管理 | 依赖管理、自动更新 | 需要发布到 npm | 个人项目 |
| CLI 工具增强 | 用户友好、功能丰富 | 需要开发 CLI | 大规模分发 |
| 自动同步服务 | 无感更新、实时同步 | 需要服务器 | 企业级使用 |

---

## 🎯 推荐方案

### 短期（1-2 周）：Git Submodule
- 简单易实现
- 版本控制完善
- 团队协作友好

### 中期（1-2 月）：npm 包管理
- 依赖管理完善
- 自动更新机制
- 个人项目友好

### 长期（3+ 月）：CLI 工具增强 + 自动同步
- 用户体验最佳
- 功能最完善
- 适合大规模分发

---

## 🔧 实现步骤

### 第一步：Git Submodule 实现

```bash
# 1. 在用户项目中添加 submodule
git submodule add https://github.com/lennney/skills.git .claude/skills

# 2. 创建更新脚本
cat > scripts/update-skills.sh << 'EOF'
#!/bin/bash
echo "Updating skills..."
cd .claude/skills
git pull origin main
cd ../..
git add .claude/skills
git commit -m "chore: update skills to latest version"
echo "Skills updated successfully!"
EOF

chmod +x scripts/update-skills.sh

# 3. 添加到 package.json
cat > package.json << 'EOF'
{
  "scripts": {
    "update-skills": "./scripts/update-skills.sh"
  }
}
EOF

# 4. 使用
npm run update-skills
```

### 第二步：版本锁定

```bash
# 锁定到特定版本
cd .claude/skills
git checkout v1.0.0
cd ../..
git add .claude/skills
git commit -m "chore: lock skills to v1.0.0"
```

### 第三步：自动更新检查

```bash
# 创建检查脚本
cat > scripts/check-skills-update.sh << 'EOF'
#!/bin/bash
echo "Checking for skills updates..."
cd .claude/skills
git fetch origin
LOCAL=$(git rev-parse HEAD)
REMOTE=$(git rev-parse origin/main)

if [ "$LOCAL" != "$REMOTE" ]; then
  echo "New version available!"
  echo "Run 'npm run update-skills' to update."
else
  echo "Skills are up to date."
fi
EOF

chmod +x scripts/check-skills-update.sh

# 添加到 package.json
cat > package.json << 'EOF'
{
  "scripts": {
    "update-skills": "./scripts/update-skills.sh",
    "check-skills-update": "./scripts/check-skills-update.sh"
  }
}
EOF
```

---

## 📝 使用文档

### 安装技能
```bash
# 方法 1：Git Submodule（推荐）
git submodule add https://github.com/lennney/skills.git .claude/skills

# 方法 2：npm 包
npm install @lennney/skills
```

### 更新技能
```bash
# 方法 1：Git Submodule
npm run update-skills

# 方法 2：npm 包
npm update @lennney/skills
```

### 检查更新
```bash
npm run check-skills-update
```

### 锁定版本
```bash
cd .claude/skills
git checkout v1.0.0
cd ../..
git add .claude/skills
git commit -m "chore: lock skills to v1.0.0"
```

---

## 🎯 总结

### 推荐路径
1. **立即实现**：Git Submodule 方案
2. **短期优化**：添加更新脚本和版本锁定
3. **中期规划**：发布为 npm 包
4. **长期愿景**：CLI 工具增强 + 自动同步

### 预期效果
- **用户体验**：从手动更新 → 自动/一键更新
- **版本控制**：从无版本 → 语义化版本管理
- **团队协作**：从个人使用 → 团队共享
- **维护成本**：从高 → 低

这个优化方案将显著提升 Skills 系统的可维护性和用户体验。
