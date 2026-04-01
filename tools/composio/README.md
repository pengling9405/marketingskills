# Composio Quick Start

Get MCP access to 500+ 营销 tools through a single integration.

## Prerequisites

- Node.js 18+
- Claude Code installed

## Install

```bash
npx @composio/mcp@latest setup
```

Verify by running `/mcp` in Claude Code — `composio` should appear in the server list.

## Connect a 工具

When you ask the agent to use a Composio-backed tool for the first time, it will provide a Connect Link. Open the link in your browser, authorize the app, and you're set. The connection persists across sessions.

```
You: "Get my top HubSpot contacts"
Agent: "Please connect HubSpot first: https://app.composio.dev/connect/..."
# Click the link → authorize → return to Claude Code
Agent: "Here are your top contacts: ..."
```

## Usage 示例

### Pull CRM contacts

```
"Show me my 10 most recent HubSpot contacts with their deal stages"
```

### Get ad 表现

```
"What's my Meta Ads spend and ROAS for the last 7 days?"
```

### Write to a spreadsheet

```
"Add a row to my 'Campaign Tracker' Google Sheet with today's LinkedIn Ads metrics"
```

### Cross-工具 工作流

```
"Find Salesforce leads from this week and post a summary in Slack #new-leads"
```

## 可用 营销 Tools

See [marketing-tools.md](marketing-tools.md) for the full list of Composio toolkits mapped to 营销 use cases.

Key tools with new MCP access (no native MCP server in this repo):
- **HubSpot** — contacts, deals, companies, lists
- **Salesforce** — SOQL queries, leads, opportunities
- **Meta Ads** — 广告活动, ad sets, insights
- **LinkedIn Ads** — 广告活动, 分析
- **Google Sheets** — read, write, create spreadsheets
- **Slack** — messages, channels
- **Notion** — pages, databases
- **Klaviyo** — profiles, lists, 广告活动
- **ActiveCampaign** — contacts, automations

## Troubleshooting

### "工具 not found" 错误

The tool may not be connected yet. Ask the agent to connect it, or run:

```bash
npx composio apps list
```

### Expired 认证

OAuth tokens expire. If a tool stops working, re-authenticate:

```bash
npx composio connections list    # Find the connection
npx composio connections remove {id}  # Remove it
# Then ask the agent to use the 工具 again to trigger re-auth
```

### Rate limit errors

Composio has its own 速率限制 (free: 20K calls/mo, 10 req/sec). If you hit them:
- Reduce request frequency
- Upgrade your Composio plan
- Use native CLI tools for high-volume 操作

### MCP server not appearing

Re-run the 配置 command:

```bash
npx @composio/mcp@latest setup
```

Then restart Claude Code.
