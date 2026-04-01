# Livestorm

视频 engagement 平台 for webinars, virtual events, and online meetings with built-in 分析 and integrations.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Events, Sessions, People, Recordings, Webhooks |
| MCP | - | 不可用 |
| CLI | ✓ | [livestorm.js](../clis/livestorm.js) |
| SDK | - | REST API with JSON:API format |

## 认证方式

- **类型**: API Token
- **请求头**: `Authorization: {API_TOKEN}` (no prefix)
- **Content-类型**: `application/vnd.api+json` (JSON:API)
- **作用域**: Identity, Events, Admin, Webhooks
- **获取令牌**： 账户 Settings > Integrations > Public API
- **Docs**: https://developers.livestorm.co/

## 常见代理操作

### Ping (测试 认证)

```bash
GET https://api.livestorm.co/v1/ping

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### List events

```bash
GET https://api.livestorm.co/v1/events?page[number]=1&page[size]=25

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### Create an 事件

```bash
POST https://api.livestorm.co/v1/events

Headers:
  Authorization: {API_TOKEN}
  Content-Type: application/vnd.api+json

{
  "data": {
    "type": "events",
    "attributes": {
      "title": "Product Demo Webinar",
      "slug": "product-demo-webinar",
      "estimated_duration": 60
    }
  }
}
```

### Get 事件 details

```bash
GET https://api.livestorm.co/v1/events/{event_id}

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### Update an 事件

```bash
PATCH https://api.livestorm.co/v1/events/{event_id}

Headers:
  Authorization: {API_TOKEN}
  Content-Type: application/vnd.api+json

{
  "data": {
    "type": "events",
    "id": "{event_id}",
    "attributes": {
      "title": "Updated Webinar Title"
    }
  }
}
```

### List sessions

```bash
GET https://api.livestorm.co/v1/sessions?page[number]=1&page[size]=25

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### Create a 会话 for an 事件

```bash
POST https://api.livestorm.co/v1/events/{event_id}/sessions

Headers:
  Authorization: {API_TOKEN}
  Content-Type: application/vnd.api+json

{
  "data": {
    "type": "sessions",
    "attributes": {
      "estimated_started_at": "2025-06-15T14:00:00.000Z",
      "timezone": "America/New_York"
    }
  }
}
```

### Register someone for a 会话

```bash
POST https://api.livestorm.co/v1/sessions/{session_id}/people

Headers:
  Authorization: {API_TOKEN}
  Content-Type: application/vnd.api+json

{
  "data": {
    "type": "people",
    "attributes": {
      "fields": {
        "email": "attendee@example.com",
        "first_name": "Jane",
        "last_name": "Doe"
      }
    }
  }
}
```

### List 会话 participants

```bash
GET https://api.livestorm.co/v1/sessions/{session_id}/people?page[number]=1&page[size]=25

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### Remove a registrant from 会话

```bash
DELETE https://api.livestorm.co/v1/sessions/{session_id}/people?filter[email]=attendee@example.com

Headers:
  Authorization: {API_TOKEN}
```

### List 会话 chat messages

```bash
GET https://api.livestorm.co/v1/sessions/{session_id}/chat-messages

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### List 会话 questions

```bash
GET https://api.livestorm.co/v1/sessions/{session_id}/questions

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### 获取会话录屏

```bash
GET https://api.livestorm.co/v1/sessions/{session_id}/recordings

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### List all people

```bash
GET https://api.livestorm.co/v1/people?page[number]=1&page[size]=25

Headers:
  Authorization: {API_TOKEN}
  Accept: application/vnd.api+json
```

### Create a webhook

```bash
POST https://api.livestorm.co/v1/webhooks

Headers:
  Authorization: {API_TOKEN}
  Content-Type: application/vnd.api+json

{
  "data": {
    "type": "webhooks",
    "attributes": {
      "target_url": "https://example.com/webhook",
      "event_name": "attendance"
    }
  }
}
```

## API 模式

Livestorm follows the JSON:API specification:
- All responses use `data`, `attributes`, `relationships` structure
- Pagination: `page[number]` and `page[size]` query parameters
- Filtering: `filter[field]=value` query parameters
- Events contain multiple Sessions; Sessions contain People
- ISO 8601 timestamps throughout

## 核心指标

### 事件 指标
- `title` - 事件 title
- `slug` - URL-friendly identifier
- `estimated_duration` - Duration in minutes
- `registration_page_enabled` - Registration page status
- `everyone_can_speak` - Whether all attendees can speak

### 会话 指标
- `status` - Session status (upcoming, live, past)
- `estimated_started_at` - Scheduled start time
- `started_at` - Actual start time
- `ended_at` - Actual end time
- `timezone` - Session timezone
- `attendees_count` - Number of attendees
- `registrants_count` - Number of registrants

### People 指标
- `email` - Contact email
- `first_name` / `last_name` - Contact name
- `registrant_detail` - Registration metadata
- `attendance_rate` - Attendance percentage
- `attended_at` - Join timestamp
- `left_at` - Leave timestamp

## Parameters

### Pagination
- `page[number]` - Page number (default: 1)
- `page[size]` - Items per page (default: 25)

### 事件 Attributes
- `title` - 事件 title (required for create)
- `slug` - URL slug
- `description` - 事件 description
- `estimated_duration` - Duration in minutes

### 会话 Attributes
- `estimated_started_at` - ISO 8601 start time
- `timezone` - IANA timezone string

### Registration Fields
- `email` - Registrant email (required)
- `first_name` - First name
- `last_name` - Last name

### Webhook Events
- `attendance` - Triggered on session attendance
- `registration` - Triggered on new registration
- `unregistration` - Triggered on unregistration

## 适用场景

- Hosting 产品 demos and 营销 webinars
- Automated webinar registration and attendee 管理
- 跟踪 webinar engagement and attendance rates
- Retrieving session recordings for content repurposing
- Building custom registration pages with API-driven registration
- Syncing webinar data with CRM and 营销 automation
- Monitoring session Q&A and chat for follow-up

## 速率限制

- **10,000 API calls per 30-day period** (organization-wide)
- 速率限制 shared across all API tokens in the organization
- Plan accordingly for high-volume 操作
- Use webhooks instead of polling to conserve quota

## 相关技能

- webinar-营销
- 事件-营销
- lead-generation
- content-strategy
- lifecycle-营销
- 客户-engagement
