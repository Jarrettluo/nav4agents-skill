---
name: nav4agents
description: "AI Agent 导航工具，汇聚优秀的 AI Agent、MCP 服务器与智能工具。用于查询和发现：(1) MCP 服务器信息（如 GitHub MCP、Filesystem MCP、Brave Search MCP 等），(2) AI Skills 信息（如 Auto Code Review、API Docs Generator、Unit Test Generator 等），(3) AI 编码工具对比（Codex、Cursor、Windsurf）。当用户需要查找 AI 工具、MCP 服务器、Skills 或对比 AI 编码工具时使用此技能。"
---

# Nav4Agents 查询

用于查询 nav4agents.com 上的 MCP 服务器、AI Skills 和智能工具信息。

## 网站信息

**网址**: https://nav4agents.com

### 主要版块

1. **MCP 生态** - https://nav4agents.com/mcp
   - 开发工具、效率工具、AI 增强、内容处理、数据处理、垂直行业

2. **AI Skills** - https://nav4agents.com/skills
   - 开发辅助、内容处理等各类 AI 技能

3. **智能工具对比** - https://nav4agents.com/subscriptions
   - 主流 AI 编码工具对比（Codex 免费、Cursor $20/月、Windsurf $15/月）

## 查询方法

使用 web_fetch 工具获取最新信息：

```python
# 查询 MCP 服务器列表
web_fetch(url="https://nav4agents.com/mcp")

# 查询 AI Skills 列表
web_fetch(url="https://nav4agents.com/skills")

# 查询特定 MCP 详情（如 GitHub MCP）
web_fetch(url="https://nav4agents.com/mcp/github-mcp")

# 查询特定 Skill 详情（如 Auto Code Review）
web_fetch(url="https://nav4agents.com/skills/auto-code-review")
```

## 数据来源

- 热门 MCP 服务器：GitHub MCP (1250⭐)、Filesystem MCP (980⭐)、Brave Search MCP (820⭐)、Notion MCP (890⭐)
- 热门 AI Skills：Auto Code Review (3200次使用)、Git Workflow Helper (2200次使用)、Unit Test Generator (2100次使用)、API Docs Generator (1800次使用)

## 使用场景

- 用户需要查找特定功能的 MCP 服务器
- 用户需要发现新的 AI Skills
- 用户想对比主流 AI 编码工具
- 用户想了解某个 MCP 或 Skill 的详细信息

直接访问对应页面获取最新内容。