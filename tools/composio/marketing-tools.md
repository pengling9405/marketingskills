# Composio Marketing Tools

这里详细映射了 Composio toolkits 与营销使用场景的关系，分类方式与 [REGISTRY.md](../REGISTRY.md) 保持一致。

## CRM

| Composio Toolkit | 认证 | 关键营销操作 | 覆盖深度 |
|-----------------|------|-------------|----------|
| `HUBSPOT` | OAuth 2.0 | 获取 / 创建联系人、按阶段列出 deal、获取公司信息、管理列表、按属性搜索联系人 | Deep |
| `SALESFORCE` | OAuth 2.0 | 执行 SOQL 查询、获取 / 创建 leads、列出 opportunities、获取账户详情、更新记录 | Deep |

## Email & SMS

| Composio Toolkit | 认证 | 关键营销操作 | 覆盖深度 |
|-----------------|------|-------------|----------|
| `ACTIVECAMPAIGN` | API Key | 获取联系人、列出 automations、把联系人加入列表、获取 campaign 数据 | Medium |
| `KLAVIYO` | API Key | 获取 profiles、列出 segments、获取 campaign 指标、加入列表 | Medium |
| `MAILCHIMP` | OAuth 2.0 | 获取 audience、列出 campaign、读取 campaign report、添加订阅者 | Deep |
| `GMAIL` | OAuth 2.0 | 发邮件、搜索收件箱、读取消息、管理标签 | Deep |

## Advertising

| Composio Toolkit | 认证 | 关键营销操作 | 覆盖深度 |
|-----------------|------|-------------|----------|
| `FACEBOOKADS` | OAuth 2.0 | 获取 campaign 洞察、列出 ad set、查看广告表现、读取 audience 数据 | Medium |
| `LINKEDIN` | OAuth 2.0 | 获取 campaign analytics、列出 campaign、获取公司主页数据 | Medium |
| `GOOGLEADS` | OAuth 2.0 | 获取 campaign 表现、列出 ad group、查看关键词数据 | Medium |

## Productivity & Collaboration

| Composio Toolkit | 认证 | 关键营销操作 | 覆盖深度 |
|-----------------|------|-------------|----------|
| `GOOGLESHEETS` | OAuth 2.0 | 读写单元格、创建表格、格式化区域、追加行 | Deep |
| `SLACK` | OAuth 2.0 | 发消息、读取频道、上传文件、搜索消息 | Deep |
| `NOTION` | OAuth 2.0 | 读取 / 创建页面、查询数据库、更新 block、搜索 | Deep |
| `AIRTABLE` | OAuth 2.0 | 列出 / 创建 / 更新记录、查询视图、管理表 | Deep |

## Commerce

| Composio Toolkit | 认证 | 关键营销操作 | 覆盖深度 |
|-----------------|------|-------------|----------|
| `SHOPIFY` | OAuth 2.0 | 获取产品、列出订单、获取客户数据、读取库存水平 | Deep |

## Analytics

| Composio Toolkit | 认证 | 关键营销操作 | 覆盖深度 |
|-----------------|------|-------------|----------|
| `GOOGLEANALYTICS` | OAuth 2.0 | 运行报表、获取实时数据、列出 properties | Medium |

## 覆盖深度说明

- **Deep**：20+ 个 action，覆盖大多数常见操作，适合日常使用
- **Medium**：5-20 个 action，覆盖核心读取操作和部分写入
- **Shallow**：少于 5 个 action，只能满足基础只读场景

## 与原生工具的覆盖对比

下表展示了，相比 MarketingSkills registry 中已有的原生能力，Composio 在哪些地方有额外价值：

| 工具 | 原生 MCP | 原生 CLI | Composio MCP | 建议 |
|------|:--------:|:--------:|:------------:|------|
| HubSpot | - | ✓ | ✓ | **优先用 Composio**，因为补上了 MCP 访问 |
| Salesforce | - | ✓ | ✓ | **优先用 Composio**，因为补上了 MCP 访问 |
| Meta Ads | - | ✓ | ✓ | **优先用 Composio**，因为补上了 MCP 访问 |
| LinkedIn Ads | - | ✓ | ✓ | **优先用 Composio**，因为补上了 MCP 访问 |
| Google Sheets | - | - | ✓ | **优先用 Composio**，这是唯一 MCP 方案 |
| Slack | - | - | ✓ | **优先用 Composio**，这是唯一 MCP 方案 |
| Notion | - | - | ✓ | **优先用 Composio**，这是唯一 MCP 方案 |
| Airtable | - | - | ✓ | **优先用 Composio**，这是唯一 MCP 方案 |
| ActiveCampaign | - | ✓ | ✓ | **优先用 Composio**，因为补上了 MCP 访问 |
| Klaviyo | - | ✓ | ✓ | **优先用 Composio**，因为补上了 MCP 访问 |
| Shopify | - | ✓ | ✓ | **优先用 Composio**，因为补上了 MCP 访问 |
| Gmail | - | - | ✓ | **优先用 Composio**，这是唯一 MCP 方案 |
| GA4 | ✓ | ✓ | ✓ | **优先用原生工具**，覆盖更深 |
| Stripe | ✓ | ✓ | ✓ | **优先用原生工具**，覆盖更深 |
| Mailchimp | ✓ | ✓ | ✓ | **优先用原生工具**，覆盖更深 |
| Google Ads | ✓ | ✓ | ✓ | **优先用原生工具**，覆盖更深 |

## Toolkit 参考

每个 Composio toolkit 名都对应平台里的 `TOOL_NAME` 标识符。搜索可用 action 时，请使用这些精确名称：

```bash
# 列出某个 toolkit 的所有 action
npx composio actions list --app HUBSPOT

# 搜索特定 action
npx composio actions list --app FACEBOOKADS --search "insights"
```

如果你要看包含配置、定价和限制的完整集成指南，请查看 [composio.md](../integrations/composio.md)。
