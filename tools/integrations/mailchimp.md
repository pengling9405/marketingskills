# Mailchimp

Email 营销 平台 for 广告活动, automation, and 受众 management.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | 营销 API for 广告活动, audiences, automation |
| MCP | ✓ | 可用 via Mailchimp MCP server |
| CLI | - | 不可用 |
| SDK | ✓ | Official SDKs for multiple languages |

## 认证方式

- **类型**: API Key or OAuth 2.0
- **请求头**: `Authorization: Bearer {api_key}` or `Authorization: apikey {api_key}`
- **Base URL**: `https://{dc}.api.mailchimp.com/3.0/` (dc = datacenter from API key)

## 常见代理操作

### List audiences (lists)

```bash
GET https://{dc}.api.mailchimp.com/3.0/lists
```

### Get 受众 members

```bash
GET https://{dc}.api.mailchimp.com/3.0/lists/{list_id}/members?count=100
```

### Add subscriber

```bash
POST https://{dc}.api.mailchimp.com/3.0/lists/{list_id}/members

{
  "email_address": "user@example.com",
  "status": "subscribed",
  "merge_fields": {
    "FNAME": "John",
    "LNAME": "Doe"
  }
}
```

### Update subscriber

```bash
PATCH https://{dc}.api.mailchimp.com/3.0/lists/{list_id}/members/{subscriber_hash}

{
  "merge_fields": {
    "FNAME": "Jane"
  },
  "tags": ["customer", "premium"]
}
```

### Get 广告活动

```bash
GET https://{dc}.api.mailchimp.com/3.0/campaigns?count=20
```

### Get 广告活动 report

```bash
GET https://{dc}.api.mailchimp.com/3.0/reports/{campaign_id}
```

### Create 广告活动

```bash
POST https://{dc}.api.mailchimp.com/3.0/campaigns

{
  "type": "regular",
  "recipients": {
    "list_id": "{list_id}"
  },
  "settings": {
    "subject_line": "Your Subject",
    "from_name": "Your Name",
    "reply_to": "reply@example.com"
  }
}
```

### Send 广告活动

```bash
POST https://{dc}.api.mailchimp.com/3.0/campaigns/{campaign_id}/actions/send
```

### List automations

```bash
GET https://{dc}.api.mailchimp.com/3.0/automations
```

## 核心指标

### 广告活动 Report Fields
- `emails_sent` - Total sent
- `opens` - Open count
- `unique_opens` - Unique opens
- `open_rate` - Open rate
- `clicks` - Click count
- `click_rate` - Click rate
- `unsubscribes` - Unsubscribe count
- `bounces` - Bounce count

### Subscriber Hash

Calculate subscriber hash for updates:
```javascript
const hash = md5(email.toLowerCase());
```

## Subscriber Statuses

- `subscribed` - Active subscriber
- `unsubscribed` - Unsubscribed
- `cleaned` - Hard bounce
- `pending` - Awaiting confirmation
- `transactional` - Transactional only

## 适用场景

- Managing email lists and subscribers
- Creating and sending email 广告活动
- Setting up email automation
- Analyzing 广告活动 表现
- Segmenting audiences
- A/B 测试 emails

## 速率限制

- 10 concurrent connections
- 10 requests per second
- Batch endpoints for bulk 操作

## 相关技能

- email-sequence
- 分析-跟踪
- referral-program
