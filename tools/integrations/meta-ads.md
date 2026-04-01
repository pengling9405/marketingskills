# Meta Ads (Facebook/Instagram)

Advertising 平台 for Facebook, Instagram, Messenger, and 受众 Network.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | 营销 API for 广告活动, audiences, reporting |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | Official SDKs for Python, PHP, Node.js |

## 认证方式

- **类型**: OAuth 2.0 Access Token
- **请求头**: Access token as query parameter
- **配置方式**: Create app in Meta Business Suite, generate System User token

## 常见代理操作

### Get ad accounts

```bash
GET https://graph.facebook.com/v18.0/me/adaccounts?access_token={access_token}&fields=id,name,account_status
```

### Get 广告活动

```bash
GET https://graph.facebook.com/v18.0/act_{ad_account_id}/campaigns?access_token={access_token}&fields=id,name,status,objective,daily_budget
```

### Get 广告活动 insights

```bash
GET https://graph.facebook.com/v18.0/{campaign_id}/insights?access_token={access_token}&fields=impressions,clicks,spend,actions,cost_per_action_type&date_preset=last_30d
```

### Get ad sets

```bash
GET https://graph.facebook.com/v18.0/act_{ad_account_id}/adsets?access_token={access_token}&fields=id,name,status,targeting,daily_budget,bid_amount
```

### Get ads

```bash
GET https://graph.facebook.com/v18.0/{ad_set_id}/ads?access_token={access_token}&fields=id,name,status,creative
```

### Create 广告活动

```bash
POST https://graph.facebook.com/v18.0/act_{ad_account_id}/campaigns

access_token={access_token}
&name=Campaign Name
&objective=CONVERSIONS
&status=PAUSED
&special_ad_categories=[]
```

### Update 广告活动 status

```bash
POST https://graph.facebook.com/v18.0/{campaign_id}

access_token={access_token}
&status=ACTIVE
```

### Get custom audiences

```bash
GET https://graph.facebook.com/v18.0/act_{ad_account_id}/customaudiences?access_token={access_token}&fields=id,name,approximate_count
```

### Create lookalike 受众

```bash
POST https://graph.facebook.com/v18.0/act_{ad_account_id}/customaudiences

access_token={access_token}
&name=Lookalike - Top Customers
&subtype=LOOKALIKE
&origin_audience_id={source_audience_id}
&lookalike_spec={"type":"similarity","country":"US"}
```

## 核心指标

| 指标 | 说明 |
|--------|-------------|
| `impressions` | Ad 曝光 |
| `clicks` | All 点击 |
| `spend` | Amount spent |
| `reach` | Unique people reached |
| `frequency` | Avg 曝光 per person |
| `cpm` | Cost per 1000 曝光 |
| `cpc` | 每次点击成本 |
| `actions` | 转化 array |
| `cost_per_action_type` | CPA by action |

## 广告活动 Objectives

- `AWARENESS` - Brand awareness
- `TRAFFIC` - Website traffic
- `ENGAGEMENT` - Post engagement
- `LEADS` - Lead generation
- `APP_PROMOTION` - App installs
- `SALES` - 转化/catalog sales

## Targeting Options

```json
{
  "geo_locations": {
    "countries": ["US"],
    "cities": [{"key": "2420379"}]
  },
  "age_min": 25,
  "age_max": 45,
  "genders": [1, 2],
  "interests": [{"id": "6003139266461", "name": "Marketing"}],
  "behaviors": [{"id": "6002714895372"}]
}
```

## 适用场景

- Creating/managing Facebook and Instagram ads
- 受众 targeting and lookalikes
- 广告活动 表现 分析
- Retargeting 配置方式

## 速率限制

- 200 calls/hour per ad 账户
- 60 calls/hour for 营销 API
- Use batch requests for efficiency

## 相关技能

- paid-ads
- 分析-跟踪
- page-cro
