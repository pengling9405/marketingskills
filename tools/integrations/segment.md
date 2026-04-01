# Segment

客户 data 平台 for collecting, routing, and activating 用户数据.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | 跟踪 API, Profile API, Config API |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | 分析.js, iOS, Android, server libraries |

## 认证方式

- **跟踪**: Write Key (per 来源)
- **API**： Access Token (OAuth 2.0)
- **请求头**: `Authorization: Bearer {access_token}`

## 常见代理操作

### 跟踪事件

```bash
POST https://api.segment.io/v1/track

Authorization: Basic {base64(write_key:)}

{
  "userId": "user_123",
  "event": "signup_completed",
  "properties": {
    "plan": "pro",
    "method": "email"
  }
}
```

### 识别用户

```bash
POST https://api.segment.io/v1/identify

Authorization: Basic {base64(write_key:)}

{
  "userId": "user_123",
  "traits": {
    "email": "user@example.com",
    "name": "John Doe",
    "plan": "pro"
  }
}
```

### 跟踪页面浏览

```bash
POST https://api.segment.io/v1/page

Authorization: Basic {base64(write_key:)}

{
  "userId": "user_123",
  "name": "Pricing",
  "properties": {
    "title": "Pricing - Example",
    "url": "https://example.com/pricing"
  }
}
```

### 批量事件

```bash
POST https://api.segment.io/v1/batch

Authorization: Basic {base64(write_key:)}

{
  "batch": [
    {"type": "identify", "userId": "user_1", "traits": {"plan": "free"}},
    {"type": "track", "userId": "user_1", "event": "signup"}
  ]
}
```

### 获取用户画像 (Profile API)

```bash
GET https://profiles.segment.com/v1/spaces/{space_id}/collections/users/profiles/user_id:{user_id}/traits

Authorization: Basic {base64(access_token:)}
```

### 获取用户事件

```bash
GET https://profiles.segment.com/v1/spaces/{space_id}/collections/users/profiles/user_id:{user_id}/events

Authorization: Basic {base64(access_token:)}
```

## JavaScript SDK

```javascript
// Initialize
analytics.load('WRITE_KEY');

// Identify user
analytics.identify('user_123', {
  email: 'user@example.com',
  plan: 'pro'
});

// Track event
analytics.track('Feature Used', {
  feature_name: 'export'
});

// Page view
analytics.page('Pricing');
```

## 关键概念

- **Sources** - Where data comes from (website, app, server)
- **Destinations** - Where data goes (分析, CRM, ads)
- **跟踪 Plan** - Schema for events and properties
- **Protocols** - Data governance and validation
- **Personas** - Unified user profiles
- **Audiences** - Computed user segments

## 常见目标平台

- 分析: GA4, Mixpanel, Amplitude
- CRM: HubSpot, Salesforce
- Email: 客户.io, Mailchimp
- Ads: Google Ads, Meta
- Data Warehouse: BigQuery, Snowflake

## 适用场景

- Centralizing 事件 跟踪
- Routing data to multiple tools
- Maintaining consistent 跟踪
- Building unified user profiles
- Syncing audiences across platforms

## 速率限制

- 500 requests/second per 来源
- Batch up to 500KB or 32KB per 事件

## 相关技能

- 分析-跟踪
- email-sequence
- paid-ads
