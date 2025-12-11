# BubbleLab - 开源 AI 工作流平台

> 来源：[趣谈AI 公众号](https://mp.weixin.qq.com/s/3blWvphLekLHfNvteOBi_g)
> GitHub：https://github.com/bubblelabai/BubbleLab
> 类型：开源项目

---

## TL;DR

- 可视化工作流 + TypeScript 代码生成，兼顾易用性与生产可靠性
- 核心概念「Bubble」：可组合的集成组件（服务型/工具型/工作流型）
- 解决痛点：无代码工具难扩展、纯代码效率低、生成代码不透明

---

## 核心特性

1. **TypeScript 原生**：全链路类型安全，减少运行时错误
2. **高度可观测**：内置日志、追踪、步骤级 introspection
3. **Bubble 生态**：可组合、可分享、可 fork 的集成组件
4. **生产级运行时**：耐用、可重放、可自托管
5. **AI 原生**：支持自然语言生成工作流

---

## 技术架构

```
Apps
├── bubble-studio    # React + Vite 可视化构建器
└── bubblelab-api    # Bun + Hono 后端 API

Core Packages
├── @bubblelab/bubble-core       # 核心工作流引擎
├── @bubblelab/bubble-runtime    # 运行时执行环境
├── @bubblelab/shared-schemas    # 通用类型定义
├── @bubblelab/ts-scope-manager  # TS 作用域分析
└── create-bubblelab-app         # CLI 脚手架
```

技术栈：React、Vite、Bun、Hono、TypeScript、pnpm、Docker、SQLite

---

## 本地部署

```bash
# 前提：安装 Bun、pnpm、Node.js v18+

git clone https://github.com/bubblelabai/BubbleLab.git
cd BubbleLab
pnpm install
pnpm run dev

# 配置 apps/bubblelab-api/.env
GOOGLE_API_KEY=xxx
OPENROUTER_API_KEY=xxx
```

- 前端：http://localhost:3000
- 后端：http://localhost:3001

---

## 适用场景

- 开发者：构建可观测、可靠的 AI 工作流
- 团队/初创：替代难扩展的无代码工具
- 研究者：快速实验 AI Agent 和 API 集成

---

## 优缺点

**优点**
- 类型安全，全程 TypeScript
- 可视化 + 代码双模式
- 开源免费，无 vendor lock-in

**缺点**
- 项目早期，稳定性待验证
- Bubble 生态尚在建设
- 需配置 API 密钥才能运行

---

#tool #workflow #opensource #typescript #ai-automation
