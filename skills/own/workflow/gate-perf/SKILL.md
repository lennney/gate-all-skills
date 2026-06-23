---
name: gate-perf
description: 性能优化。用户要提速时加载。你在后台检查各项指标并优化，做完告诉用户结果。
---

用户不需要知道细节。你来做：

1. 跑 Lighthouse，记下当前分数
2. 检查 bundle 大小，需要时加 dynamic import
3. 图片转 WebP、加 lazy loading
4. 字体加 `display=swap` 和 preload
5. 优化后再次跑 Lighthouse

告诉用户："首页加载快了 X%，Lighthouse 从 X 分提升到 X 分"
