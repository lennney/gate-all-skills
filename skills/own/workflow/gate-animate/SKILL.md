---
name: gate-animate
description: ✨ 动效与交互。给网站加过渡动画、滚动动效、微交互。先 CSS 后 Framer Motion。
---

Add motion to the site in layers:

1. **页面过渡** → 路由切换 fade/slide（CSS only first）
2. **滚动动画** → 元素进入视口渐入（IntersectionObserver）
3. **微交互** → hover 反馈、loading 骨架屏
4. **进阶** → Framer Motion 复杂动效

**原则：** 动效服务体验，不动为了动。用户 `prefers-reduced-motion` 时关闭。
