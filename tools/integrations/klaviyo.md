# Klaviyo

E-commerce email and SMS 营销 平台 with profiles, flows, 广告活动, segments, and 事件 跟踪.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API with JSON:API spec, revision-versioned |
| MCP | - | 不可用 |
| CLI | ✓ | [klaviyo.js](../clis/klaviyo.js) |
| SDK | ✓ | Python, Node.js, Ruby, PHP, Java, C# |

## 认证方式

- **类型**: Private API Key
- **请求头**: `Authorization: Klaviyo-API-Key {private_api_key}`
- **Revision 请求头**: `revision: 2024-10-15` (required on all requests)
- **Get key**: 账户 Settings > API Keys at https://www.klaviyo.com/settings/账户/API-keys
- **Note**: Private keys are prefixed with `pk_`; public keys (6-char site ID) are for client-side only

## 常见代理操作

### List profiles

```bash
GET https://a.klaviyo.com/api/profiles/?page[size]=20

# Filter by email
GET https://a.klaviyo.com/api/profiles/?filter=equals(email,"user@example.com")
```

### Create profile

```bash
POST https://a.klaviyo.com/api/profiles/

{
  "data": {
    "type": "profile",
    "attributes": {
      "email": "user@example.com",
      "first_name": "Jane",
      "last_name": "Doe",
      "phone_number": "+15551234567"
    }
  }
}
```

### Update profile

```bash
PATCH https://a.klaviyo.com/api/profiles/{profileId}/

{
  "data": {
    "type": "profile",
    "id": "{profileId}",
    "attributes": {
      "first_name": "Updated Name"
    }
  }
}
```

### List all lists

```bash
GET https://a.klaviyo.com/api/lists/
```

### Create list

```bash
POST https://a.klaviyo.com/api/lists/

{
  "data": {
    "type": "list",
    "attributes": {
      "name": "Newsletter Subscribers"
    }
  }
}
```

### Add profiles to list

```bash
POST https://a.klaviyo.com/api/lists/{listId}/relationships/profiles/

{
  "data": [
    { "type": "profile", "id": "{profileId1}" },
    { "type": "profile", "id": "{profileId2}" }
  ]
}
```

### 跟踪事件

```bash
POST https://a.klaviyo.com/api/events/

{
  "data": {
    "type": "event",
    "attributes": {
      "metric": {
        "data": {
          "type": "metric",
          "attributes": { "name": "Placed Order" }
        }
      },
      "profile": {
        "data": {
          "type": "profile",
          "attributes": { "email": "user@example.com" }
        }
      },
      "properties": {
        "value": 99.99,
        "items": ["Product A"]
      },
      "time": "2025-01-15T10:00:00Z"
    }
  }
}
```

### 列出广告活动

```bash
GET https://a.klaviyo.com/api/campaigns/?filter=equals(messages.channel,"email")
```

### List flows

```bash
GET https://a.klaviyo.com/api/flows/
```

### Update flow status

```bash
PATCH https://a.klaviyo.com/api/flows/{flowId}/

{
  "data": {
    "type": "flow",
    "id": "{flowId}",
    "attributes": {
      "status": "live"
    }
  }
}
```

### List 指标

```bash
GET https://a.klaviyo.com/api/metrics/
```

### List segments

```bash
GET https://a.klaviyo.com/api/segments/
```

## API Pattern

Klaviyo uses the JSON:API specification. All request/response bodies use `{ "data": { "type": "...", "attributes": {...} } }` format. Relationships are managed via `/relationships/` sub-endpoints. The `revision` 请求头 is required on every request and determines API behavior version.

## 核心指标

### Profile Fields
- `email` - Email address
- `phone_number` - Phone for SMS
- `first_name`, `last_name` - Name fields
- `properties` - Custom properties object
- `subscriptions` - Email/SMS subscription status

### 事件 Fields
- `metric` - The metric/事件 name
- `properties` - Custom 事件 properties
- `time` - 事件 timestamp
- `value` - Monetary value (for revenue 跟踪)

### 广告活动/Flow 指标
- `send_count` - Number of sends
- `open_rate` - Open percentage
- `click_rate` - Click percentage
- `revenue` - Attributed revenue

## Parameters

### 常见 Query Parameters
- `page[size]` - Results per page (default 20, max 100)
- `page[cursor]` - Cursor for pagination
- `filter` - Filter expressions (e.g., `equals(email,"user@example.com")`)
- `sort` - Sort field (prefix `-` for descending)
- `include` - Include related resources
- `fields[resource]` - Sparse fieldsets

## 适用场景

- E-commerce email/SMS 营销 automation
- Syncing 客户 profiles from external systems
- 跟踪 purchase events and 客户 behavior
- Managing email flows and drip 广告活动
- Segmenting audiences for targeted 广告活动
- Reporting on 广告活动 and flow 表现

## 速率限制

- Steady-state: 75 requests/second for most endpoints
- Burst: up to 700 requests in 1 minute
- Rate limit 请求头: `RateLimit-Limit`, `RateLimit-Remaining`, `RateLimit-Reset`
- Lower limits on some write endpoints (profiles, events)

## 相关技能

- email-sequence
- ecommerce-email
- lifecycle-营销
- 客户-segmentation
