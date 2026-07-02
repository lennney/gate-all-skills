---
name: gate-ci
description: "CI/CD 配置。用户说"配 CI"、"自动化部署"、"加 GitHub Actions"时加载。配置 GitHub Actions / GitLab CI，自动跑测试、lint、构建。"
trigger: 需要配置 CI/CD
input: 项目配置
output: CI/CD 配置
next: 无
dependencies: 无
---

1. 帮用户确认 GitHub 仓库已连接
2. 引导用户在 Vercel 点 Import
3. 配置 main 分支自动部署 + PR 预览

告诉用户：
"配置好了。以后你只要把代码推送到 GitHub 的 main 分支，网站就会自动更新上线——不用再手动构建、上传了。如果你开了一个 PR（修改请求），Vercel 会自动生成一个预览链接，你可以先看看效果再合并。"
