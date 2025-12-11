# Claude Code MCP 配置

添加 fetch MCP server:

```bash
claude mcp add fetch -s user -- npx mcp-fetch-server
```

如果需要设置环境变量 DEFAULT_LIMIT:

```bash
claude mcp add fetch -s user -e DEFAULT_LIMIT=150000 -- npx mcp-fetch-server
```

查看已配置的 MCP servers:

```bash
claude mcp list
```
