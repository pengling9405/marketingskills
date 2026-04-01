# DataForSEO

Comprehensive SEO data API for SERP results, 关键词 research, backlinks, and on-page analysis.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | SERP, 关键词 Data, Backlinks, On-Page, Labs |
| MCP | - | 不可用 |
| CLI | ✓ | [dataforseo.js](../clis/dataforseo.js) |
| SDK | ✓ | Python, TypeScript, PHP, Java, C# |

## 认证方式

- **类型**: Basic Auth
- **请求头**: `Authorization: Basic {base64(login:password)}`
- **Get credentials**: API Access tab at https://app.dataforseo.com/API-access
- **Note**: API password is auto-generated, different from 账户 password

## 常见代理操作

### SERP - Google organic (live)

```bash
POST https://api.dataforseo.com/v3/serp/google/organic/live/regular

[{
  "keyword": "marketing automation",
  "location_name": "United States",
  "language_name": "English"
}]
```

### 关键词 - 搜索 volume (live)

```bash
POST https://api.dataforseo.com/v3/keywords_data/google_ads/search_volume/live

[{
  "keywords": ["email marketing", "marketing automation", "crm software"],
  "location_code": 2840,
  "language_code": "en"
}]
```

### 关键词 - 关键词 for site (live)

```bash
POST https://api.dataforseo.com/v3/keywords_data/google_ads/keywords_for_site/live

[{
  "target": "example.com",
  "location_code": 2840,
  "language_code": "en"
}]
```

### Backlinks - Summary

```bash
POST https://api.dataforseo.com/v3/backlinks/summary/live

[{
  "target": "example.com",
  "internal_list_limit": 10,
  "backlinks_status_type": "live"
}]
```

### Backlinks - List

```bash
POST https://api.dataforseo.com/v3/backlinks/backlinks/live

[{
  "target": "example.com",
  "mode": "as_is",
  "limit": 100,
  "backlinks_status_type": "live"
}]
```

### Backlinks - Referring domains

```bash
POST https://api.dataforseo.com/v3/backlinks/referring_domains/live

[{
  "target": "example.com",
  "limit": 100
}]
```

### Backlinks - Index (database stats)

```bash
GET https://api.dataforseo.com/v3/backlinks/index
```

### On-Page - Instant pages audit

```bash
POST https://api.dataforseo.com/v3/on_page/instant_pages

[{
  "url": "https://example.com/page",
  "enable_javascript": true
}]
```

### SERP - Locations list

```bash
GET https://api.dataforseo.com/v3/serp/google/locations
```

### SERP - Languages list

```bash
GET https://api.dataforseo.com/v3/serp/google/languages
```

## API Pattern

DataForSEO uses two methods for most endpoints:
- **Live** (`/live`) - Synchronous, results in same response
- **Task-based** (`/task_post` + `/task_get/$id`) - Async for large requests

Request bodies are always JSON arrays (even for single requests).

## 核心指标

### 关键词 指标
- `search_volume` - Monthly 搜索 volume
- `competition` - Competition level (0-1)
- `cpc` - 每次点击成本
- `monthly_searches` - Monthly breakdown array

### Backlink 指标
- `total_backlinks` - Total backlink count
- `referring_domains` - Unique referring domains
- `domain_rank` - Domain 权威 score
- `backlinks_spam_score` - Spam score

## 适用场景

- Programmatic SERP 跟踪 at scale
- 关键词 research with 搜索 volume data
- Backlink analysis and monitoring
- On-page SEO audits
- Competitor 分析

## 速率限制

- Rate limit 请求头: `X-RateLimit-Limit`, `X-RateLimit-Remaining`
- Backlinks API: 2000 requests/minute, 30 simultaneous
- Varies by endpoint and plan

## 相关技能

- seo-audit
- programmatic-seo
- content-strategy
- competitor-alternatives
