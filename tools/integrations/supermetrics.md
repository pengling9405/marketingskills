# Supermetrics

营销 data pipeline that connects 200+ 营销 platforms. Pulls data from ad platforms, 分析, social, SEO, email, and more into a single query interface.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Query any connected data 来源, manage accounts |
| MCP | ✓ | [Claude connector](https://claude.com/connectors/supermetrics) |
| CLI | ✓ | [supermetrics.js](../clis/supermetrics.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: API Key
- **Query param**: `api_key={api_key}` or **请求头**: `x-api-key: {api_key}`
- **Get key**: Supermetrics Hub > API settings at https://hub.supermetrics.com

## 常见代理操作

### Query a Data 来源

```bash
POST https://api.supermetrics.com/enterprise/v2/query/data/json

{
  "ds_id": "GA4",
  "ds_accounts": "123456789",
  "date_range_type": "last_28_days",
  "fields": [
    { "name": "sessions" },
    { "name": "pageviews" },
    { "name": "date" }
  ]
}
```

### Query with Filters

```bash
POST https://api.supermetrics.com/enterprise/v2/query/data/json

{
  "ds_id": "AW",
  "ds_accounts": "123-456-7890",
  "date_range_type": "last_month",
  "fields": [
    { "name": "campaign_name" },
    { "name": "clicks" },
    { "name": "impressions" },
    { "name": "cost" }
  ],
  "max_rows": 100
}
```

### List 可用 Data Sources

```bash
GET https://api.supermetrics.com/enterprise/v2/datasources
```

### List Connected Accounts

```bash
GET https://api.supermetrics.com/enterprise/v2/datasources/accounts?ds_id=GA4
```

### List Teams

```bash
GET https://api.supermetrics.com/enterprise/v2/teams
```

### List 用户

```bash
GET https://api.supermetrics.com/enterprise/v2/users
```

## 核心指标

### Data 来源 IDs
- `GA4` - Google 分析 4
- `GA4_PAID` - Google 分析 (paid)
- `AW` - Google Ads
- `FB` - Facebook Ads
- `LI` - LinkedIn Ads
- `TW_ADS` - Twitter Ads
- `IG_IA` - Instagram
- `FB_IA` - Facebook Pages
- `GSC` - Google 搜索 Console
- `SE` - Semrush
- `MC` - Mailchimp
- `HubSpot` - HubSpot

### Date Range Values
- `last_28_days` - Last 28 days
- `last_month` - Previous calendar month
- `this_month` - Current month to date
- `custom` - Custom range (requires `start_date` and `end_date`)

## Parameters

### Query
- `ds_id` - Data 来源 identifier (required)
- `ds_accounts` - 账户 ID for the data 来源 (required)
- `date_range_type` - Date range preset or "custom" (required)
- `fields` - Array of field objects with `name` property (required)
- `filter` - Filter expression for narrowing results
- `max_rows` - Maximum number of rows to return
- `start_date` - Start date for custom range (YYYY-MM-DD)
- `end_date` - End date for custom range (YYYY-MM-DD)

### 常见 Fields by 来源
- **GA4**: `sessions`, `pageviews`, `users`, `bounce_rate`, `date`, `source`, `medium`, `page_path`
- **Google Ads**: `campaign_name`, `clicks`, `impressions`, `cost`, `conversions`, `ctr`, `cpc`
- **Facebook Ads**: `campaign_name`, `impressions`, `clicks`, `spend`, `reach`, `cpm`, `cpc`
- **LinkedIn Ads**: `campaign_name`, `impressions`, `clicks`, `cost`, `conversions`
- **GSC**: `query`, `clicks`, `impressions`, `ctr`, `position`, `page`

## 适用场景

- Pulling cross-平台 营销 data into a single report
- Comparing 表现 across ad platforms (Google, Meta, LinkedIn, TikTok)
- Aggregating 分析 data from multiple sources
- Automating 营销 reporting 工作流
- Building unified dashboards across 营销 channels
- Extracting SEO data alongside paid media 指标

## 速率限制

- 速率限制 vary by plan
- Enterprise API: typically 100 requests/minute
- Query results may be paginated for large datasets
- Recommended: use `max_rows` to control response size

## 相关技能

- 分析-跟踪
- paid-ads
- seo-audit
- content-strategy
- social-content
