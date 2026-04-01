# 客户.io

Behavior-based messaging 平台 for email, push, SMS, and in-app.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Track API, App API, Journeys API |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | JavaScript, iOS, Android, Ruby, Python |

## 认证方式

- **Track API**: Site ID + API Key (Basic auth)
- **App API**: Bearer token
- **请求头**: `Authorization: Basic {base64(site_id:api_key)}`

## 常见代理操作

### Identify 客户

```bash
PUT https://track.customer.io/api/v1/customers/{customer_id}

Authorization: Basic {base64(site_id:api_key)}

{
  "email": "user@example.com",
  "created_at": 1705312800,
  "first_name": "John",
  "plan": "pro"
}
```

### 跟踪事件

```bash
POST https://track.customer.io/api/v1/customers/{customer_id}/events

Authorization: Basic {base64(site_id:api_key)}

{
  "name": "purchase",
  "data": {
    "product": "Pro Plan",
    "amount": 99
  }
}
```

### Track anonymous 事件

```bash
POST https://track.customer.io/api/v1/events

Authorization: Basic {base64(site_id:api_key)}

{
  "name": "page_viewed",
  "data": {
    "page": "/pricing"
  },
  "anonymous_id": "anon_123"
}
```

### Delete 客户

```bash
DELETE https://track.customer.io/api/v1/customers/{customer_id}

Authorization: Basic {base64(site_id:api_key)}
```

### Get 客户 (App API)

```bash
GET https://api.customer.io/v1/customers/{customer_id}/attributes

Authorization: Bearer {app_api_key}
```

### 列出广告活动

```bash
GET https://api.customer.io/v1/campaigns

Authorization: Bearer {app_api_key}
```

### Get 广告活动 指标

```bash
GET https://api.customer.io/v1/campaigns/{campaign_id}/metrics

Authorization: Bearer {app_api_key}
```

### Trigger broadcast

```bash
POST https://api.customer.io/v1/campaigns/{campaign_id}/triggers

Authorization: Bearer {app_api_key}

{
  "emails": ["user@example.com"],
  "data": {
    "coupon_code": "SAVE20"
  }
}
```

### Send transactional 邮件

```bash
POST https://api.customer.io/v1/send/email

Authorization: Bearer {app_api_key}

{
  "transactional_message_id": "1",
  "to": "user@example.com",
  "identifiers": {
    "id": "user_123"
  },
  "message_data": {
    "order_id": "ORD-456"
  }
}
```

## JavaScript SDK

```javascript
// Initialize
_cio.identify({
  id: 'user_123',
  email: 'user@example.com',
  created_at: 1705312800,
  plan: 'pro'
});

// Track event
_cio.track('purchase', {
  product: 'Pro Plan',
  amount: 99
});

// Track page view
_cio.page();
```

## 关键概念

- **People** - 客户 and leads
- **Segments** - Dynamic groups based on attributes/behavior
- **广告活动** - Automated message sequences
- **Broadcasts** - One-time sends
- **Transactional** - Triggered messages

## Attribute Types

- Standard: `email`, `created_at`, `unsubscribed`
- Custom: Any key you define
- Computed: Aggregations from events

## 适用场景

- Behavior-based email automation
- Multi-channel messaging (email, push, SMS)
- Onboarding sequences
- Re-engagement 广告活动
- Transactional messages

## 速率限制

- Track API: 100 requests/second
- App API: 10 requests/second

## 相关技能

- email-sequence
- onboarding-cro
- 分析-跟踪
