# AI-Note

用 Claude Code + MCP 自动整理 AI 文章到 Obsidian 知识库。

## 快速开始

### 1. 安装 Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

### 2. 配置 MCP（fetch 工具）

在 `~/.claude/settings.json` 中添加：

```json
{
  "mcpServers": {
    "fetch": {
      "command": "uvx",
      "args": ["mcp-server-fetch"]
    }
  }
}
```

需要先安装 uv：
```bash
# macOS
brew install uv

# 或 pip
pip install uv
```

### 3. 运行

```bash
cd /path/to/AI-Note
claude
```

## 使用方法

在 Claude Code 中发送文章链接，会自动整理到对应目录：

```
https://example.com/ai-article
```

或明确指定：
```
https://example.com/ai-article 整理到知识库
```

## 目录结构

```
AI-Note/
├── 00_Inbox/      # 未分类
├── 10_Models/     # 模型相关
├── 20_Tools/      # 工具相关
├── 30_Products/   # 产品相关
├── 40_Concepts/   # 概念相关
├── CLAUDE.md      # Agent 指令
└── README.md
```

## 自定义

编辑 `CLAUDE.md` 可修改：
- 分类规则
- 笔记模板
- 触发条件
