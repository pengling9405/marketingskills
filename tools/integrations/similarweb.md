# Similarweb

Competitive traffic intelligence 平台 providing website 分析, traffic sources, 关键词 data, and competitor insights.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Traffic, 搜索, Referrals, Competitors, Geography |
| MCP | - | 不可用 |
| CLI | ✓ | [similarweb.js](../clis/similarweb.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: API Key
- **Query param**: `?api_key={key}`
- **Get key**: 账户 Settings > API at https://账户.similarweb.com

## 常见代理操作

### Total Visits

```bash
GET https://api.similarweb.com/v1/website/example.com/total-traffic-and-engagement/visits?api_key={key}&start_date=2024-01&end_date=2024-03&country=us&granularity=monthly
```

### Pages Per Visit

```bash
GET https://api.similarweb.com/v1/website/example.com/total-traffic-and-engagement/pages-per-visit?api_key={key}&start_date=2024-01&end_date=2024-03
```

### Average Visit Duration

```bash
GET https://api.similarweb.com/v1/website/example.com/total-traffic-and-engagement/average-visit-duration?api_key={key}&start_date=2024-01&end_date=2024-03
```

### Bounce Rate

```bash
GET https://api.similarweb.com/v1/website/example.com/total-traffic-and-engagement/bounce-rate?api_key={key}&start_date=2024-01&end_date=2024-03
```

### Traffic Sources Breakdown

```bash
GET https://api.similarweb.com/v1/website/example.com/traffic-sources/overview?api_key={key}&start_date=2024-01&end_date=2024-03
```

### Top Referral Sites

```bash
GET https://api.similarweb.com/v1/website/example.com/traffic-sources/referrals?api_key={key}&start_date=2024-01&end_date=2024-03
```

### Organic 关键词

```bash
GET https://api.similarweb.com/v1/website/example.com/search/organic-search-keywords?api_key={key}&start_date=2024-01&end_date=2024-03
```

### Paid 关键词

```bash
GET https://api.similarweb.com/v1/website/example.com/search/paid-search-keywords?api_key={key}&start_date=2024-01&end_date=2024-03
```

### Similar Sites / Competitors

```bash
GET https://api.similarweb.com/v1/website/example.com/similar-sites/similarsites?api_key={key}
```

### Category Ranking

```bash
GET https://api.similarweb.com/v1/website/example.com/category-rank/category-rank?api_key={key}
```

### Traffic by Country

```bash
GET https://api.similarweb.com/v1/website/example.com/geo/traffic-by-country?api_key={key}&start_date=2024-01&end_date=2024-03
```

## 核心指标

### Traffic & Engagement
- `visits` - Total visits for the period
- `pages_per_visit` - Average pages viewed per visit
- `average_visit_duration` - Average session duration in seconds
- `bounce_rate` - Percentage of single-page visits

### Traffic Sources
- `search` - Organic + paid 搜索 percentage
- `social` - Social media traffic percentage
- `direct` - Direct traffic percentage
- `referrals` - Referral traffic percentage
- `mail` - Email traffic percentage
- `display_ads` - 展示 advertising percentage

### 搜索 关键词
- `search_term` - 关键词 text
- `share` - Traffic share percentage
- `volume` - 搜索 volume
- `cpc` - 每次点击成本
- `position` - Average ranking position

### Geography
- `country` - Country code
- `share` - Traffic share from that country

## Parameters

### 常见 Parameters
- `start_date` - Start month (YYYY-MM format)
- `end_date` - End month (YYYY-MM format)
- `country` - Two-letter country code (e.g., us, gb, de)
- `granularity` - Data granularity: monthly, weekly, daily

### 搜索 Parameters
- `limit` - Number of 关键词 to return
- `country` - Filter by country

## 适用场景

- Analyzing competitor website traffic and engagement 指标
- Benchmarking your site against competitors
- Identifying top traffic sources for any website
- Discovering competitor organic and paid 关键词
- Finding similar sites and competitive landscape
- Understanding geographic traffic distribution
- Auditing SEO 表现 relative to competitors
- Researching market share by traffic volume

## 速率限制

- 速率限制 vary by plan tier
- Standard: 10 requests/second
- Data availability depends on plan (3 months to 36 months historical)
- Some endpoints require Premium or Enterprise plans

## 相关技能

- seo-audit
- competitor-alternatives
- paid-ads
- content-strategy
