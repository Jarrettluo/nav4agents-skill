---
name: nav4agents
description: "Nav4Agents（nav4agents.com）数据查询：MCP 服务器、AI Skills 与 Coding Plan 套餐。用于查找、发现、对比 AI Agent 工具。数据每周一自动更新，支持直接读取静态 JSON（页面为客户端渲染，抓 HTML 拿不到列表数据）。"
---

# Nav4Agents 查询

nav4agents.com 是 AI Agent 工具导航站，提供 MCP 服务器、AI Skills 与 Coding Plan 的结构化数据。

**查询要点：页面为客户端渲染，直接抓 HTML 拿不到列表数据 → 优先读取静态 JSON。**

## 静态 JSON 接口（免鉴权，每周一自动更新）

| 数据 | 地址 | 条目数 |
|---|---|---|
| MCP 服务器 | https://nav4agents.com/data/mcp.json | ~200 |
| AI Skills | https://nav4agents.com/data/skills.json | ~165 |
| 编程套餐对比 | https://nav4agents.com/data/codingplan.json | ~75 |
| 热门 MCP 详情 | https://nav4agents.com/data/mcp-details.json | ~120 |
| 元信息 | https://nav4agents.com/data/meta.json | counts + scannedAt |

### 主要字段

- **mcp.json**: id, name, slug, description, category, type(local|remote), url, installCmd, stars(热度; 0=官方收录), featured, source, smitheryId, verified
- **skills.json**: id, name, slug, ownerHandle, description, category, installCmd(clawhub install @owner/slug), usage(下载量), topics, version, changelog, url
- **codingplan.json**: platform, plan, link, firstMonthPrice, monthlyPrice, quarterlyPrice, yearlyPrice, models[], fiveHourRequests, weeklyRequests, monthlyRequests, rating
- **mcp-details.json**（按 slug 索引）: tools[{name,description}], config[{name,required,description}], remoteUrl, iconUrl, verified

## 使用示例

```python
import requests

# 1) 关键词搜索 MCP / Skills
mcps = [m for m in requests.get('https://nav4agents.com/data/mcp.json').json()
        if 'search' in (m['name'] + m['description']).lower()]

# 2) 热度 Top MCP
top = sorted([m for m in requests.get('https://nav4agents.com/data/mcp.json').json() if m['stars']],
             key=lambda m: -m['stars'])[:10]

# 3) 编程套餐按月费排序
plans = requests.get('https://nav4agents.com/data/codingplan.json').json()
def num(p):
    d = ''.join(c for c in p['monthlyPrice'] if c.isdigit() or c == '.')
    return float(d) if d else 1e9
cheap = sorted(plans, key=num)[:10]
```

## 网页入口

- MCP: https://nav4agents.com/mcp（详情 `/mcp/<slug>`，含工具列表与配置项）
- Skills: https://nav4agents.com/skills（详情 `/skills/<slug>`，含版本说明）
- 套餐对比: https://nav4agents.com/codingplan
- 订阅工具: https://nav4agents.com/subscriptions

## 数据来源与更新

- MCP: Smithery Registry（热度）+ MCP 官方注册表
- Skills: ClawHub（按下载量排序）
- 套餐: wmpeng/codingplan
- 每周一自动扫描更新（扫描时点见 meta.json → scannedAt）
- 站点收藏为浏览器本地存储（无账号体系）