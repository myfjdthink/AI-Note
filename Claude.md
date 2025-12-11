# 项目：AI 文章 → Obsidian 知识库整理 Agent

## 总体目标

你在本项目中的主要任务是：

- 当我给出 **AI 相关文章的链接** 并说明要“整理/记录/存到 Obsidian / 知识库”时，
- 自动：
  1. 抓取网页正文；
  2. 理解和分类文章（模型 / 工具 / 产品 / 概念 / 其它）；
  3. 用约定好的 Markdown 模板生成一篇阅读笔记（中文为主）；
  4. 按分类写入到 **当前项目目录（即 Obsidian Vault 根目录）** 下对应文件夹中。

除非我明确说要做别的事（比如写代码、调接口等），否则对“整理文章到 Obsidian”的请求都按这里的流程来做。

---

## 运行环境 & 路径约定

- 假设：当前工作目录就是一个 Obsidian Vault 的根目录（例如 `AI-Knowledge`）。
- 本文件 `CLAUDE.md` 就放在这个根目录里。
- 所有文件操作都使用 **相对路径**，不要写绝对路径（避免写到奇怪的位置）。

### 分类对应的目录

请按 `category` 把笔记写到以下目录（不存在就创建目录）：

- `model`    → `10_Models/`
- `tool`     → `20_Tools/`
- `product`  → `30_Products/`
- `concept`  → `40_Concepts/`
- 其他无法判断 → `00_Inbox/`

---

## 触发条件：什么时候启用“文章整理工作流”

当用户消息满足以下任意条件时，启用“文章整理到 Obsidian”的工作流：

- 消息中包含一个或多个 `http://` 或 `https://` 链接，且
- 同时包含类似表述：
  - “整理到 Obsidian”
  - “记到知识库”
  - “帮我做读书笔记 / 阅读笔记”
  - “帮我归档这篇文章”
  - “加入 AI 知识库”
- 或者我明确说：“以后我给你的 AI 文章链接，默认都按这个工作流记到 Obsidian”。

如果我只是问“这篇文章讲什么”“帮我翻译一下”，而没有提到 Obsidian / 知识库，就按普通问答处理，不要写文件。

---

## 标准流程：处理 AI 文章链接

### 步骤 1：抓取网页正文

1. 对每个链接依次处理。
2. 使用 MCP 的 **`fetch_txt`** 工具抓取网页纯文本内容：
   - 调用 `fetch_txt` 并传入 URL
   - 提取：
     - `title`（页面标题）
     - `main_content`（正文文本，剔除导航、评论、广告）
     - 可能的 `author`、`published_at`、`site_name`。
3. 如果抓取失败：
   - 简单重试一次；
   - 仍失败则在对话中说明失败原因，不写 Obsidian 文件。

> 要点：正文提取只需在你的"思考"里完成，不必生成单独文件。

---

### 步骤 2：理解 & 结构化文章

在内部先把文章信息整理成一个 **JSON 结构**（用于你自己思考，不必真的创建 `.json` 文件），字段示例：

```jsonc
{
  "url": "https://example.com/ai-article",
  "title": "Sample Article Title",
  "site_name": "Example Blog",
  "author": "Author Name",
  "origin_published_at": "2025-10-01",
  "category": "model",      // model | tool | product | concept | other
  "subtype": "opensource-llm", // 可选，如 agent-framework / prompt-engineering 等
  "tldr_bullets": [
    "用 3~5 条要点总结文章核心结论，中文",
    "要突出对实际落地的启发"
  ],
  "background": "文章要解决的动机 / 问题背景（中文简述）",
  "core_idea": "核心方案 / 模型 / 系统设计（中文简述，可带小标题）",
  "strengths": [
    "列出文章或方案的优势",
    "和现有主流方案相比有什么不同"
  ],
  "limitations": [
    "方案的局限 / 前提假设 / 风险",
    "作者没讲但你推理出的潜在坑点"
  ],
  "use_cases": [
    "适用场景 1",
    "适用场景 2"
  ],
  "project_links": {
    "ads3": ["和去中心化广告协议相关的启发（如有就写）"],
    "task3": ["和任务/Quest 产品相关的启发（如有就写）"]
  },
  "sub_tags": ["agent", "tooling", "vector-db"],
  "outline": [
    "I. 文章大纲第一部分",
    "II. 文章大纲第二部分"
  ],
  "quotes": [
    "可以保留 1~3 句英文原文或你用中文转述的关键句"
  ]
}
