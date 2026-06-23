---
name: gate-perf
description: ⚡ 性能优化。加载 performance 技能，检查 Lighthouse、Bundle、图片、字体。
---

Load `performance` skill. Check these in order:

1. **Lighthouse 跑分** → 目标 Desktop > 95, Mobile > 85
2. **Bundle** → 检查大依赖，需要时加 dynamic import
3. **图片** → next/image, WebP, 懒加载
4. **字体** → `display=swap`, preload 关键字体
5. **Core Web Vitals** → LCP < 2.5s, CLS < 0.1

做完跑一次 `npm run build` + Lighthouse 确认提升。
