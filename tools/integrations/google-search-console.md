# Google 搜索 Console

Free tool for monitoring website 搜索 表现 and indexing.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | 搜索 分析 API, URL Inspection API |
| MCP | - | 不可用 |
| CLI | - | Use gcloud or API scripts |
| SDK | ✓ | Google API client libraries |

## 认证方式

- **类型**: OAuth 2.0 or Service 账户
- **作用域**: `https://www.googleapis.com/auth/webmasters.readonly`
- **配置**: Create credentials in Google Cloud Console

## 常见代理操作

### Get 搜索 分析

```bash
POST https://searchconsole.googleapis.com/webmasters/v3/sites/{site_url}/searchAnalytics/query

{
  "startDate": "2024-01-01",
  "endDate": "2024-01-31",
  "dimensions": ["query"],
  "rowLimit": 100
}
```

### Get 表现 by 页面

```bash
POST https://searchconsole.googleapis.com/webmasters/v3/sites/{site_url}/searchAnalytics/query

{
  "startDate": "2024-01-01",
  "endDate": "2024-01-31",
  "dimensions": ["page"],
  "rowLimit": 50
}
```

### Get 表现 by country

```bash
POST https://searchconsole.googleapis.com/webmasters/v3/sites/{site_url}/searchAnalytics/query

{
  "startDate": "2024-01-01",
  "endDate": "2024-01-31",
  "dimensions": ["country", "query"],
  "rowLimit": 100
}
```

### Inspect URL

```bash
POST https://searchconsole.googleapis.com/v1/urlInspection/index:inspect

{
  "inspectionUrl": "https://example.com/page",
  "siteUrl": "https://example.com/"
}
```

### List sitemaps

```bash
GET https://searchconsole.googleapis.com/webmasters/v3/sites/{site_url}/sitemaps

Authorization: Bearer {access_token}
```

### Submit sitemap

```bash
PUT https://searchconsole.googleapis.com/webmasters/v3/sites/{site_url}/sitemaps/{sitemap_url}

Authorization: Bearer {access_token}
```

### Request indexing

```bash
POST https://indexing.googleapis.com/v3/urlNotifications:publish

{
  "url": "https://example.com/new-page",
  "type": "URL_UPDATED"
}
```

## Dimensions

- `query` - 搜索 query
- `page` - Page URL
- `country` - Country code
- `device` - Device 类型 (MOBILE, DESKTOP, TABLET)
- `date` - Date
- `searchAppearance` - 搜索 result 类型

## 指标

- `clicks` - 点击 from 搜索
- `impressions` - 搜索 曝光
- `ctr` - 点击率
- `position` - Average position

## Filters

```json
{
  "dimensionFilterGroups": [{
    "filters": [{
      "dimension": "query",
      "operator": "contains",
      "expression": "keyword"
    }]
  }]
}
```

## 适用场景

- Analyzing 搜索 表现
- Finding 关键词 opportunities
- Monitoring indexing status
- Submitting new pages for indexing
- Identifying crawl issues
- 跟踪 position changes

## 速率限制

- 200 queries per minute
- 1,200 requests per minute

## 相关技能

- seo-audit
- programmatic-seo
- 分析-跟踪
