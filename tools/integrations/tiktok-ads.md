# TikTok Ads

Advertising 平台 for TikTok's short-form 视频 受众.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | 营销 API for 广告活动, audiences, reporting |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | Python SDK available |

## 认证方式

- **类型**: Access Token
- **请求头**: `Access-Token: {access_token}`
- **配置方式**: Create app in TikTok for Business, get access token

## 常见代理操作

### Get advertiser info

```bash
GET https://business-api.tiktok.com/open_api/v1.3/advertiser/info/?advertiser_ids=["{advertiser_id}"]

Access-Token: {access_token}
```

### Get 广告活动

```bash
GET https://business-api.tiktok.com/open_api/v1.3/campaign/get/?advertiser_id={advertiser_id}&page=1&page_size=20

Access-Token: {access_token}
```

### Get 广告活动 报告

```bash
POST https://business-api.tiktok.com/open_api/v1.3/report/integrated/get/

Access-Token: {access_token}

{
  "advertiser_id": "{advertiser_id}",
  "report_type": "BASIC",
  "dimensions": ["campaign_id"],
  "metrics": ["spend", "impressions", "clicks", "conversion"],
  "data_level": "AUCTION_CAMPAIGN",
  "start_date": "2024-01-01",
  "end_date": "2024-01-31"
}
```

### Create 广告活动

```bash
POST https://business-api.tiktok.com/open_api/v1.3/campaign/create/

Access-Token: {access_token}

{
  "advertiser_id": "{advertiser_id}",
  "campaign_name": "Campaign Name",
  "objective_type": "CONVERSIONS",
  "budget_mode": "BUDGET_MODE_DAY",
  "budget": 100
}
```

### Update 广告活动 状态

```bash
POST https://business-api.tiktok.com/open_api/v1.3/campaign/status/update/

Access-Token: {access_token}

{
  "advertiser_id": "{advertiser_id}",
  "campaign_ids": ["{campaign_id}"],
  "opt_status": "ENABLE"
}
```

### Get ad groups

```bash
GET https://business-api.tiktok.com/open_api/v1.3/adgroup/get/?advertiser_id={advertiser_id}&campaign_ids=["{campaign_id}"]

Access-Token: {access_token}
```

### Get audiences

```bash
GET https://business-api.tiktok.com/open_api/v1.3/dmp/custom_audience/list/?advertiser_id={advertiser_id}

Access-Token: {access_token}
```

## 核心指标

| 指标 | 说明 |
|--------|-------------|
| `spend` | Amount spent |
| `impressions` | Ad 曝光 |
| `clicks` | 点击 |
| `ctr` | 点击率 |
| `cpc` | 每次点击成本 |
| `cpm` | Cost per 1000 曝光 |
| `conversion` | 转化 |
| `cost_per_conversion` | CPA |
| `video_play_actions` | 视频 views |
| `video_watched_6s` | 6s views |

## 广告活动 Objectives

- `REACH` - Brand awareness
- `TRAFFIC` - Website traffic
- `VIDEO_VIEWS` - 视频 views
- `LEAD_GENERATION` - Lead forms
- `CONVERSIONS` - Website 转化
- `APP_PROMOTION` - App installs

## Targeting Options

### Demographics
- Age ranges
- Gender
- Languages
- Locations

### Interests & Behavior
- Interest categories
- 视频 interactions
- Creator interactions
- Hashtag interactions

### Custom Audiences
- 客户 file uploads
- Website visitors (pixel)
- App activity
- Engagement audiences

## 适用场景

- Reaching younger demographics (18-34)
- 视频-first advertising
- Viral/creative 广告活动
- App promotion

## 速率限制

- 10 requests/second
- 100,000 requests/day

## 相关技能

- paid-ads
- 分析-跟踪
