# Skyvern

> AI 驱动的浏览器自动化工具，用视觉+LLM理解网页，无需 XPath

## 元信息

| 字段 | 值 |
|------|-----|
| 来源 | [51Testing软件测试网](https://mp.weixin.qq.com/s/AsxyGNuo133h04QFwsDZkg) |
| 分类 | tool |
| 子类型 | browser-automation |
| 标签 | #agent #automation #browser #vision-llm |

---

## TL;DR

- Skyvern 是一款浏览器自动化工具，核心创新是**不依赖 XPath/DOM 解析，而是用视觉+LLM"看"网页**
- 灵感来自 BabyAGI 和 AutoGPT 的任务驱动自主代理设计，底层使用 Playwright
- 面向最终用户，无需编程，提供可视化工作流界面
- 适合网站经常改版、页面结构复杂的场景，能大幅降低维护成本

---

## 背景

传统浏览器自动化（如 Selenium）依赖 XPath 或 CSS 选择器定位元素，网页结构一变就容易失效，维护成本高。Skyvern 尝试用 AI 视觉理解来解决这个问题。

---

## 核心方案

### 工作原理

- 采用多智能体协作架构（受 BabyAGI/AutoGPT 启发）
- 用视觉模型+LLM 理解网页内容，而非解析 DOM
- 底层通过 Playwright 执行实际的浏览器操作

### 核心能力

1. **在从未见过的网站上执行任务**
2. **网页布局变化时依然保持鲁棒性**
3. **基于 LLM 理解进行逻辑推理**（如根据页面内容自动判断选项）

---

## 优势

- 无需编程，可视化搭建工作流
- 模拟真实用户行为，不易被反爬机制识别
- 网站改版时无需频繁维护脚本
- 开箱即用，适合非技术人员

---

## 局限

- 依赖 LLM 调用，可能有延迟和成本
- 复杂交互场景的准确性待验证
- 对于需要精细控制的开发者场景，不如 Chrome DevTools MCP 灵活

---

## 适用场景

- 定期下载发票、对账单
- 批量填写表单、提交申请
- 跨平台数据收集和比价
- 定期检查网站状态变化
- 网站经常改版、页面结构复杂的自动化任务

---

## 对比：Skyvern vs Chrome DevTools MCP

| 维度 | Skyvern | Chrome DevTools MCP |
|------|---------|---------------------|
| 定位 | 面向最终用户的"自动化工人" | 面向开发者的"自动化工具" |
| 使用门槛 | 无需编程，开箱即用 | 需要编写代码/指令 |
| 输出 | 解决方案 | 构建解决方案的工具 |

---

## 安装使用

```bash
# 依赖：Python 3.11+, Node.js, npm
pip install skyvern
skyvern quickstart
skyvern run all
# 访问 http://localhost:8080
```

---

## 相关链接

- 原文：https://mp.weixin.qq.com/s/AsxyGNuo133h04QFwsDZkg
