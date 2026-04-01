# Firehose

Real-time web data streaming API that monitors web pages and delivers matching content instantly via server-sent events (SSE). Built for competitive intelligence, brand monitoring, and news 跟踪 without polling.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | RESTful endpoints for managing rules + SSE for streaming |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | - | Native AI agent skill available |

## 认证方式

- **类型**: API Key
- **Currently**: Free beta — no credit card required
- **Get access**: Sign up at firehose.com

## Core 概念

**Rules** — Filters that define what content to match. Uses Lucene query syntax.

**Stream** — A server-sent 事件 (SSE) connection that delivers matching content in real-time as it's published on the web.

Instead of polling an endpoint on a schedule, you define rules once and receive a continuous stream of matches as they happen.

## Query Syntax (Lucene)

```
# Exact phrase
"your brand name"

# Field-specific
title:tesla
domain:reuters.com
domain:techcrunch.com

# Boolean operators
"Series A" AND (SaaS OR software)
competitor OR "competitor name" NOT "your company"

# Wildcard
market* AND funding

# Language filter
language:en

# Date range
publish_time:[2026-01-01 TO 2026-03-18]

# ML-classified categories
category:finance
category:technology
```

## 常见代理操作

### Create a monitoring rule

```bash
POST https://api.firehose.com/rules

{
  "query": "\"your brand name\" OR \"your product name\"",
  "label": "brand-mentions"
}
```

### List active rules

```bash
GET https://api.firehose.com/rules
```

### Delete a rule

```bash
DELETE https://api.firehose.com/rules/{rule_id}
```

### Connect to the stream

```bash
GET https://api.firehose.com/stream
Authorization: Bearer {api_key}

# Returns server-sent events:
# data: {"url": "...", "title": "...", "publish_time": "...", "matched_rule": "..."}
```

### 示例: Node.js stream consumer

```javascript
import EventSource from 'eventsource';

const stream = new EventSource('https://api.firehose.com/stream', {
  headers: { Authorization: `Bearer ${process.env.FIREHOSE_API_KEY}` }
});

stream.onmessage = (event) => {
  const item = JSON.parse(event.data);
  console.log(`[${item.matched_rule}] ${item.title} — ${item.url}`);
};
```

## Use Cases for 营销

### Competitive intelligence
Monitor competitors' press coverage, 产品 announcements, and funding news in real-time.

```
query: "CompetitorName" AND (launch OR funding OR "product update" OR partnership)
```

### Brand monitoring
Track mentions of your brand across news and web content.

```
query: "YourBrand" OR "YourProductName" NOT site:yourdomain.com
```

### Category / market news
Stay current on your market without manually checking sources.

```
query: category:technology AND ("no-code" OR "low-code") AND funding
domain:techcrunch.com OR domain:venturebeat.com
```

### Lead trigger monitoring
Track signals that indicate a prospect is ready to buy (hiring, funding, tool mentions).

```
query: ("hiring" OR "we're growing") AND "RevOps" AND (HubSpot OR Salesforce)
```

### PR and link building
Get alerted when publications cover topics in your space, enabling timely outreach.

```
query: "best [category] tools" OR "top [category] software" AND publish_time:[now-7d TO now]
```

## 适用场景

- Real-time competitive intelligence (faster than Google Alerts)
- Brand mention monitoring across news and web
- Market signal 跟踪 for sales prospecting
- Automated content curation pipelines
- Trigger-based 工作流 (new mention → Slack alert, CRM update, etc.)

## 相关技能

- competitor-alternatives
- 客户-research
- content-strategy
- cold-email
- marketing-ideas
