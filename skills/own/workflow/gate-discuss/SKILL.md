---
name: gate-discuss
description: 探讨阶段。同事还不知道要做什么时加载。用 grill-me / domain-modeling 的方式帮他理清需求。
disable-model-invocation: true
---

Interview the user to clarify their website project. Ask one question at a time.

**Must clarify before proceeding:**

1. **用户是谁？** — 目标用户、他们从哪里来、想在网站上做什么
2. **核心功能？** — 最少要有什么才能上线？第一版只做最核心的
3. **内容？** — 文案、图片、Logo 准备好了吗？
4. **技术选型？** — 默认推荐 Next.js + Tailwind + shadcn/ui + Vercel，有特殊需求再调整

**产出要求：** 帮用户写出一句话描述，例如："一个 Fatekeeper 游戏攻略站，展示评分、系统需求、FAQ，引导去 Steam 购买。"

聊清楚了就引导用户去 `/gate-init`。
