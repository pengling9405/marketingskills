# SavvyCal

Scheduling 平台 API for managing scheduling links, events, availability slots, and webhooks.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API v1 - scheduling links, events, webhooks |
| MCP | - | 不可用 |
| CLI | ✓ | [savvycal.js](../clis/savvycal.js) |
| SDK | - | No official SDK |

## 认证方式

- **类型**: Bearer Token (Personal Access Token or OAuth 2.0)
- **请求头**: `Authorization: Bearer {token}`
- **Get key**: Developer Settings in SavvyCal dashboard (create a Personal Access Token)

## 常见代理操作

### Get current user

```bash
GET https://api.savvycal.com/v1/me
```

### List scheduling links

```bash
GET https://api.savvycal.com/v1/scheduling-links
```

### Get a scheduling link

```bash
GET https://api.savvycal.com/v1/scheduling-links/{id}
```

### Create a scheduling link

```bash
POST https://api.savvycal.com/v1/scheduling-links

{
  "name": "30 Minute Meeting",
  "slug": "30min",
  "duration_minutes": 30
}
```

### Update a scheduling link

```bash
PATCH https://api.savvycal.com/v1/scheduling-links/{id}

{
  "name": "Updated Meeting Name"
}
```

### Delete a scheduling link

```bash
DELETE https://api.savvycal.com/v1/scheduling-links/{id}
```

### Duplicate a scheduling link

```bash
POST https://api.savvycal.com/v1/scheduling-links/{id}/duplicate
```

### Toggle link state (active/disabled)

```bash
POST https://api.savvycal.com/v1/scheduling-links/{id}/toggle
```

### Get available time slots

```bash
GET https://api.savvycal.com/v1/scheduling-links/{id}/slots
```

### List events

```bash
GET https://api.savvycal.com/v1/events
```

### Get an 事件

```bash
GET https://api.savvycal.com/v1/events/{id}
```

### Create an 事件

```bash
POST https://api.savvycal.com/v1/events

{
  "scheduling_link_id": "{link_id}",
  "start_at": "2024-01-20T10:00:00Z",
  "name": "John Doe",
  "email": "john@example.com"
}
```

### Cancel an 事件

```bash
POST https://api.savvycal.com/v1/events/{id}/cancel
```

### List webhooks

```bash
GET https://api.savvycal.com/v1/webhooks
```

### Create a webhook

```bash
POST https://api.savvycal.com/v1/webhooks

{
  "url": "https://example.com/webhook",
  "events": ["event.created", "event.canceled"]
}
```

## 核心指标

### Scheduling Link Data
- `id` - Unique link identifier
- `name` - 展示 name
- `slug` - URL slug
- `duration_minutes` - Meeting duration
- `state` - Active or disabled
- `url` - Full scheduling URL

### 事件 Data
- `id` - Unique 事件 identifier
- `name` - Invitee name
- `email` - Invitee email
- `start_at` / `end_at` - 事件 timing
- `status` - 事件 status
- `scheduling_link` - Associated scheduling link

## Parameters

### List Events
- `before` / `after` - Pagination cursors
- `limit` - Results per page (default 20, max 100)

### List Scheduling Links
- `before` / `after` - Pagination cursors
- `limit` - Results per page

## 适用场景

- Managing scheduling links programmatically
- Retrieving booked events for CRM or 分析 sync
- Checking available time slots for custom booking UIs
- Automating scheduling link creation for 广告活动
- Monitoring booking activity via webhooks

## 速率限制

- Not officially documented
- Implement retry logic with exponential backoff
- Monitor for HTTP 429 responses

## 相关技能

- lead-generation
- sales-automation
- appointment-scheduling
- 客户-onboarding
