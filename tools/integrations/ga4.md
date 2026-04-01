# Google 分析 4 (GA4)

Web 分析 平台 for 跟踪 user behavior, 转化, and 营销 表现.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Data API for reports, Admin API for configuration |
| MCP | ✓ | 可用 via Google 分析 MCP server |
| CLI | - | Use gcloud for some 操作 |
| SDK | ✓ | gtag.js, Google 分析 SDK for mobile |

## 认证方式

- **类型**: OAuth 2.0 or Service 账户
- **作用域**: `https://www.googleapis.com/auth/analytics.readonly` (read), `https://www.googleapis.com/auth/analytics.edit` (write)
- **配置方式**: Create credentials in Google Cloud Console

## 常见代理操作

### Run a report (Data API)

```bash
POST https://analyticsdata.googleapis.com/v1beta/properties/{property_id}:runReport

{
  "dateRanges": [{"startDate": "30daysAgo", "endDate": "today"}],
  "dimensions": [{"name": "sessionSource"}],
  "metrics": [{"name": "sessions"}, {"name": "conversions"}]
}
```

### Get real-time data

```bash
POST https://analyticsdata.googleapis.com/v1beta/properties/{property_id}:runRealtimeReport

{
  "dimensions": [{"name": "country"}],
  "metrics": [{"name": "activeUsers"}]
}
```

### List conversion events

```bash
GET https://analyticsadmin.googleapis.com/v1beta/properties/{property_id}/conversionEvents
```

### Create a conversion 事件

```bash
POST https://analyticsadmin.googleapis.com/v1beta/properties/{property_id}/conversionEvents

{
  "eventName": "purchase"
}
```

## Client-Side 跟踪

### Send custom 事件 (gtag.js)

```javascript
gtag('event', 'signup_completed', {
  'method': 'email',
  'plan': 'free'
});
```

### Send 事件 via 衡量 Protocol

```bash
POST https://www.google-analytics.com/mp/collect?measurement_id={measurement_id}&api_secret={api_secret}

{
  "client_id": "client_123",
  "events": [{
    "name": "purchase",
    "params": {
      "value": 99.99,
      "currency": "USD"
    }
  }]
}
```

## Key Dimensions & 指标

### 常见 Dimensions
- `sessionSource` - Traffic 来源
- `sessionMedium` - Traffic medium
- `sessionCampaignName` - 广告活动 name
- `landingPage` - Entry page
- `deviceCategory` - Device 类型
- `country` - User country

### 常见 指标
- `sessions` - Total sessions
- `activeUsers` - Active users
- `newUsers` - New users
- `conversions` - Conversion events
- `engagementRate` - Engaged sessions rate
- `averageSessionDuration` - Session duration

## 适用场景

- 跟踪 website traffic and user behavior
- Measuring 营销 广告活动 表现
- Setting up conversion 跟踪
- Analyzing user journeys and funnels
- Attribution modeling

## 速率限制

- Data API: 10 requests per second per property
- Admin API: Varies by endpoint
- 衡量 Protocol: 1M hits/day for free tier

## 相关技能

- 分析-跟踪
- ab-test-配置方式
- seo-audit
- page-cro
