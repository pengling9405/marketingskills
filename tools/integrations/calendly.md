# Calendly

Scheduling and booking 平台 API for managing 事件 types, scheduled events, invitees, and availability.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API v2 - 事件 types, scheduled events, invitees, availability |
| MCP | - | 不可用 |
| CLI | ✓ | [calendly.js](../clis/calendly.js) |
| SDK | ✓ | No official SDK; community libraries available |

## 认证方式

- **类型**: Bearer Token (Personal Access Token or OAuth 2.0)
- **请求头**: `Authorization: Bearer {token}`
- **Get key**: https://calendly.com/integrations/api_webhooks (Personal Access Token)

## 常见代理操作

### Get current user

```bash
GET https://api.calendly.com/users/me
```

### List 事件 types

```bash
GET https://api.calendly.com/event_types?user={user_uri}
```

### List scheduled events

```bash
GET https://api.calendly.com/scheduled_events?user={user_uri}&min_start_time=2024-01-01T00:00:00Z&max_start_time=2024-12-31T23:59:59Z&status=active
```

### Get a scheduled 事件

```bash
GET https://api.calendly.com/scheduled_events/{event_uuid}
```

### List invitees for an 事件

```bash
GET https://api.calendly.com/scheduled_events/{event_uuid}/invitees
```

### Cancel a scheduled 事件

```bash
POST https://api.calendly.com/scheduled_events/{event_uuid}/cancellation

{
  "reason": "Cancellation reason"
}
```

### Get available times

```bash
GET https://api.calendly.com/event_type_available_times?event_type={event_type_uri}&start_time=2024-01-20T00:00:00Z&end_time=2024-01-27T00:00:00Z
```

### Get user busy times

```bash
GET https://api.calendly.com/user_busy_times?user={user_uri}&start_time=2024-01-20T00:00:00Z&end_time=2024-01-27T00:00:00Z
```

### List organization members

```bash
GET https://api.calendly.com/organization_memberships?organization={organization_uri}
```

### Create webhook subscription

```bash
POST https://api.calendly.com/webhook_subscriptions

{
  "url": "https://example.com/webhook",
  "events": ["invitee.created", "invitee.canceled"],
  "organization": "{organization_uri}",
  "scope": "organization"
}
```

### List webhook subscriptions

```bash
GET https://api.calendly.com/webhook_subscriptions?organization={organization_uri}&scope=organization
```

### Delete webhook subscription

```bash
DELETE https://api.calendly.com/webhook_subscriptions/{webhook_uuid}
```

## 核心指标

### Scheduled 事件 Data
- `uri` - Unique 事件 URI
- `name` - 事件 类型 name
- `status` - 事件 status (active, canceled)
- `start_time` / `end_time` - 事件 timing
- `event_type` - URI of the 事件 类型
- `location` - Meeting location details
- `invitees_counter` - Count of invitees (active, limit, total)

### Invitee Data
- `name` - Invitee full name
- `email` - Invitee email
- `status` - active or canceled
- `questions_and_answers` - Custom question responses
- `tracking` - UTM parameters
- `created_at` / `updated_at` - Timestamps

## Parameters

### List Scheduled Events
- `user` - User URI (required)
- `min_start_time` / `max_start_time` - Date range filter (ISO 8601)
- `status` - Filter by status (active, canceled)
- `count` - Number of results (default 20, max 100)
- `page_token` - Pagination token
- `sort` - Sort order (start_time:asc or start_time:desc)

### List 事件 Types
- `user` - User URI
- `organization` - Organization URI
- `active` - Filter active/inactive
- `count` - Results per page
- `sort` - Sort order

## 适用场景

- Retrieving scheduled meeting data for CRM sync
- Monitoring booking activity and conversion rates
- Automating follow-up 工作流 after meetings
- Checking availability before suggesting meeting times
- 跟踪 meeting cancellations and no-shows
- Building custom booking interfaces

## 速率限制

- Not officially documented; implement retry logic with exponential backoff
- Use conservative request rates (avoid bursting)
- Monitor for HTTP 429 responses

## 相关技能

- lead-generation
- sales-automation
- 客户-onboarding
- appointment-scheduling
