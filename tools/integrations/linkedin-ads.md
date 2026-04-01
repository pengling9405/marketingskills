# LinkedIn Ads

B2B advertising 平台 with professional targeting.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | 营销 API for 广告活动, audiences, 分析 |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | - | API-only (community libraries available) |

## 认证方式

- **类型**: OAuth 2.0
- **请求头**: `Authorization: Bearer {access_token}`
- **作用域**: `r_ads`, `r_ads_reporting`, `rw_ads`

## 常见代理操作

### Get ad accounts

```bash
GET https://api.linkedin.com/v2/adAccountsV2?q=search

Authorization: Bearer {access_token}
```

### Get 广告活动

```bash
GET https://api.linkedin.com/v2/adCampaignsV2?q=search&search.account.values[0]=urn:li:sponsoredAccount:{account_id}

Authorization: Bearer {access_token}
```

### Get 广告活动 分析

```bash
GET https://api.linkedin.com/v2/adAnalyticsV2?q=analytics&pivot=CAMPAIGN&dateRange.start.year=2024&dateRange.start.month=1&dateRange.start.day=1&dateRange.end.year=2024&dateRange.end.month=1&dateRange.end.day=31&campaigns=urn:li:sponsoredCampaign:{campaign_id}&fields=impressions,clicks,costInLocalCurrency,conversions

Authorization: Bearer {access_token}
```

### Create 广告活动

```bash
POST https://api.linkedin.com/v2/adCampaignsV2

Authorization: Bearer {access_token}

{
  "account": "urn:li:sponsoredAccount:{account_id}",
  "name": "Campaign Name",
  "type": "SPONSORED_UPDATES",
  "costType": "CPC",
  "unitCost": {
    "amount": "5.00",
    "currencyCode": "USD"
  },
  "dailyBudget": {
    "amount": "100.00",
    "currencyCode": "USD"
  },
  "status": "PAUSED"
}
```

### Update 广告活动 状态

```bash
POST https://api.linkedin.com/v2/adCampaignsV2/{campaign_id}

Authorization: Bearer {access_token}

{
  "patch": {
    "$set": {
      "status": "ACTIVE"
    }
  }
}
```

### Get creatives

```bash
GET https://api.linkedin.com/v2/adCreativesV2?q=search&search.campaign.values[0]=urn:li:sponsoredCampaign:{campaign_id}

Authorization: Bearer {access_token}
```

### Get 受众 counts

```bash
POST https://api.linkedin.com/v2/audienceCountsV2

{
  "audienceCriteria": {
    "include": {
      "and": [{
        "or": {
          "urn:li:adTargetingFacet:titles": ["urn:li:title:123"]
        }
      }]
    }
  }
}
```

## 核心指标

| 指标 | 说明 |
|--------|-------------|
| `impressions` | Ad 曝光 |
| `clicks` | Total 点击 |
| `costInLocalCurrency` | Spend |
| `conversions` | Conversion count |
| `leadGenerationMailContactInfoShares` | Lead form submissions |

## 广告活动 Types

- `SPONSORED_UPDATES` - Sponsored content
- `TEXT_AD` - Text ads
- `SPONSORED_INMAILS` - Message ads
- `DYNAMIC` - Dynamic ads

## Targeting Options

### Job-Based
- Job titles
- Job functions
- Seniority levels
- Years of experience

### Company-Based
- Company names
- Industries
- Company size
- Company followers

### Professional
- Skills
- Groups
- Schools
- Degrees

## 适用场景

- B2B advertising
- Job title targeting
- 账户-based 营销
- Lead generation 广告活动

## 速率限制

- 100 requests/day (basic)
- 10,000 requests/day (营销 Developer 平台)

## 相关技能

- paid-ads
- 分析-跟踪
