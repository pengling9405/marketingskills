# 关键词 Everywhere

关键词 research API for 搜索 volume, CPC, competition, related 关键词, and traffic data.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for 关键词 data, related 关键词, traffic |
| MCP | - | Community MCP server available |
| CLI | ✓ | [keywords-everywhere.js](../clis/keywords-everywhere.js) |
| SDK | - | API-only |

## 认证方式

- **类型**: API Key (Bearer token)
- **请求头**: `Authorization: Bearer {api_key}`
- **Get key**: https://keywordseverywhere.com/first-install-addon.html
- **Limit**: 100 关键词 per request

## 常见代理操作

### Get 关键词 data (volume, CPC, competition)

```bash
POST https://api.keywordseverywhere.com/v1/get_keyword_data

Authorization: Bearer {api_key}

{
  "country": "us",
  "currency": "USD",
  "dataSource": "gkp",
  "kw": ["email marketing", "marketing automation", "crm software"]
}
```

### Get related 关键词

```bash
POST https://api.keywordseverywhere.com/v1/get_related_keywords

Authorization: Bearer {api_key}

{
  "country": "us",
  "currency": "USD",
  "dataSource": "gkp",
  "kw": ["email marketing"]
}
```

### Get "People Also 搜索 For" 关键词

```bash
POST https://api.keywordseverywhere.com/v1/get_pasf_keywords

Authorization: Bearer {api_key}

{
  "country": "us",
  "currency": "USD",
  "dataSource": "gkp",
  "kw": ["email marketing"]
}
```

### Get domain 关键词 (what a domain ranks for)

```bash
POST https://api.keywordseverywhere.com/v1/get_domain_keywords

Authorization: Bearer {api_key}

{
  "country": "us",
  "currency": "USD",
  "domain": "example.com"
}
```

### Get URL 关键词 (what a specific URL ranks for)

```bash
POST https://api.keywordseverywhere.com/v1/get_url_keywords

Authorization: Bearer {api_key}

{
  "country": "us",
  "currency": "USD",
  "url": "https://example.com/page"
}
```

### Get domain traffic

```bash
POST https://api.keywordseverywhere.com/v1/get_domain_traffic

Authorization: Bearer {api_key}

{
  "country": "us",
  "domain": "example.com"
}
```

### Get URL traffic

```bash
POST https://api.keywordseverywhere.com/v1/get_url_traffic

Authorization: Bearer {api_key}

{
  "country": "us",
  "url": "https://example.com/page"
}
```

### Get domain backlinks

```bash
POST https://api.keywordseverywhere.com/v1/get_domain_backlinks

Authorization: Bearer {api_key}

{
  "domain": "example.com"
}
```

### Get page backlinks

```bash
POST https://api.keywordseverywhere.com/v1/get_page_backlinks

Authorization: Bearer {api_key}

{
  "url": "https://example.com/page"
}
```

### Check credits

```bash
GET https://api.keywordseverywhere.com/v1/get_credits

Authorization: Bearer {api_key}
```

### Get supported countries

```bash
GET https://api.keywordseverywhere.com/v1/get_countries

Authorization: Bearer {api_key}
```

### Get supported currencies

```bash
GET https://api.keywordseverywhere.com/v1/get_currencies

Authorization: Bearer {api_key}
```

## 核心指标

### 关键词 Data
- `vol` - Monthly 搜索 volume
- `cpc.value` - 每次点击成本
- `competition` - Competition score
- `trend` - 12-month trend data

### Traffic Data
- `estimated_traffic` - Estimated monthly traffic
- `keywords_count` - Number of ranking 关键词

## Parameters

- `country` - Country code (us, uk, de, fr, etc.)
- `currency` - Currency code (USD, GBP, EUR, etc.)
- `dataSource` - Data 来源, default `gkp` (Google 关键词 Planner)
- `kw` - Array of 关键词 (max 100 per request)

## 适用场景

- Quick 关键词 research with volume and CPC
- Finding related 关键词 and PASF suggestions
- Analyzing domain/URL 关键词 rankings
- Traffic estimation for domains and pages
- Backlink discovery

## 速率限制

- 100 关键词 per request
- Credit-based pricing (1 credit per 关键词)

## 相关技能

- seo-audit
- content-strategy
- programmatic-seo
- competitor-alternatives
