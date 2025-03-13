---
title: Cline - 关于 Plan/Act 模式的思考
tags:
  - Cline
  - AI
categories:
  - 软件开发提效
date: 2025-03-13 23:37:00
---

1. Plan 模式和 Act 模式可以共享上下文。
2. 先在 Plan 模式迭代出满意的方案，然后在 Act 模式中执行，相比一般的 AI coding agent (直接生成代码)，可以减少因生成错误代码而造成的返工 (省时、省token)。
3. 可在 Plan 模式使用 Reasoning model (如 DeepSeek R1)，在 Act 模式使用非 Reasoning model (如 Claude 3.5 Sonnet)。如此一来，在 Planning 阶段可以节省 97% 的成本。
4. Plan/Act 模式的核心理念，可以体现在提示词、应用于其它 AI coding agent，如 Cursor。





