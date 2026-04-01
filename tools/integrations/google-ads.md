# Google Ads

Pay-per-click advertising 平台 for 搜索, 展示, and 视频 广告活动.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Google Ads API for 广告活动 management |
| MCP | ✓ | 可用 via Google Ads MCP server |
| CLI | - | Use gcloud or API scripts |
| SDK | ✓ | Client libraries for multiple languages |

## 认证方式

- **类型**: OAuth 2.0
- **作用域**: `https://www.googleapis.com/auth/adwords`
- **配置方式**: Create credentials in Google Cloud Console, link to Google Ads 账户
- **请求头**: `developer-token`, `login-customer-id` (for MCC)

## 常见代理操作

### 获取账户信息

```bash
POST https://googleads.googleapis.com/v14/customers/{customer_id}/googleAds:searchStream

{
  "query": "SELECT customer.id, customer.descriptive_name FROM customer"
}
```

### 列出广告活动

```bash
POST https://googleads.googleapis.com/v14/customers/{customer_id}/googleAds:searchStream

{
  "query": "SELECT campaign.id, campaign.name, campaign.status, campaign_budget.amount_micros FROM campaign ORDER BY campaign.id"
}
```

### 获取广告活动表现

```bash
POST https://googleads.googleapis.com/v14/customers/{customer_id}/googleAds:searchStream

{
  "query": "SELECT campaign.name, metrics.impressions, metrics.clicks, metrics.cost_micros, metrics.conversions FROM campaign WHERE segments.date DURING LAST_30_DAYS"
}
```

### 获取广告组表现

```bash
POST https://googleads.googleapis.com/v14/customers/{customer_id}/googleAds:searchStream

{
  "query": "SELECT ad_group.name, metrics.impressions, metrics.clicks, metrics.conversions FROM ad_group WHERE segments.date DURING LAST_7_DAYS"
}
```

### 获取关键词表现

```bash
POST https://googleads.googleapis.com/v14/customers/{customer_id}/googleAds:searchStream

{
  "query": "SELECT ad_group_criterion.keyword.text, metrics.impressions, metrics.clicks, metrics.average_cpc FROM keyword_view WHERE segments.date DURING LAST_30_DAYS ORDER BY metrics.clicks DESC LIMIT 50"
}
```

### 暂停广告活动

```bash
POST https://googleads.googleapis.com/v14/customers/{customer_id}/campaigns:mutate

{
  "operations": [{
    "update": {
      "resourceName": "customers/{customer_id}/campaigns/{campaign_id}",
      "status": "PAUSED"
    },
    "updateMask": "status"
  }]
}
```

### 更新预算

```bash
POST https://googleads.googleapis.com/v14/customers/{customer_id}/campaignBudgets:mutate

{
  "operations": [{
    "update": {
      "resourceName": "customers/{customer_id}/campaignBudgets/{budget_id}",
      "amountMicros": "50000000"
    },
    "updateMask": "amountMicros"
  }]
}
```

## 核心指标

| 指标 | 说明 |
|--------|-------------|
| `metrics.impressions` | Ad 曝光 |
| `metrics.clicks` | 点击 |
| `metrics.cost_micros` | Cost in micros (divide by 1M) |
| `metrics.conversions` | 转化 |
| `metrics.conversions_value` | Conversion value |
| `metrics.average_cpc` | Average 每次点击成本 |
| `metrics.ctr` | 点击率 |
| `metrics.conversion_rate` | 转化率 |

## 广告活动 Types

- `SEARCH` - 搜索 network text ads
- `DISPLAY` - 展示 network
- `SHOPPING` - 产品 shopping ads
- `VIDEO` - YouTube 视频 ads
- `PERFORMANCE_MAX` - AI-optimized across channels
- `DEMAND_GEN` - Discovery/Demand Gen

## GAQL (Google Ads Query Language)

```sql
SELECT
  campaign.name,
  metrics.clicks,
  metrics.conversions
FROM campaign
WHERE
  campaign.status = 'ENABLED'
  AND segments.date DURING LAST_30_DAYS
ORDER BY metrics.conversions DESC
LIMIT 10
```

## 适用场景

- Managing 搜索 advertising 广告活动
- Analyzing 广告活动 表现
- Adjusting budgets and bids
- 关键词 research and 管理
- Conversion 跟踪 分析

## 速率限制

- 15,000 操作 per day (basic)
- Higher limits with developer token levels

## 相关技能

- paid-ads
- 分析-跟踪
- page-cro
