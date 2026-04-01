# Demio

Webinar 平台 for hosting live, automated, and on-demand webinars with built-in registration and attendee 跟踪.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Events, Registration, Participants, Sessions |
| MCP | - | 不可用 |
| CLI | ✓ | [demio.js](../clis/demio.js) |
| SDK | ✓ | PHP (official), Ruby (community) |

## 认证方式

- **类型**: API Key + API Secret
- **请求头**: `Api-Key: {key}` and `Api-Secret: {secret}`
- **Get credentials**: 账户 Settings > API (Owner access required)
- **Docs**: https://publicdemioapi.docs.apiary.io/

## 常见代理操作

### Ping (health check)

```bash
GET https://my.demio.com/api/v1/ping

Headers:
  Api-Key: {API_KEY}
  Api-Secret: {API_SECRET}
```

### List all events

```bash
GET https://my.demio.com/api/v1/events

Headers:
  Api-Key: {API_KEY}
  Api-Secret: {API_SECRET}
```

### List events by 类型

```bash
GET https://my.demio.com/api/v1/events?type=upcoming

Headers:
  Api-Key: {API_KEY}
  Api-Secret: {API_SECRET}
```

### Get a specific 事件

```bash
GET https://my.demio.com/api/v1/event/{event_id}

Headers:
  Api-Key: {API_KEY}
  Api-Secret: {API_SECRET}
```

### Get 事件 date details

```bash
GET https://my.demio.com/api/v1/event/{event_id}/date/{date_id}

Headers:
  Api-Key: {API_KEY}
  Api-Secret: {API_SECRET}
```

### Register attendee for 事件

```bash
POST https://my.demio.com/api/v1/event/register

Headers:
  Api-Key: {API_KEY}
  Api-Secret: {API_SECRET}
  Content-Type: application/json

{
  "id": 12345,
  "name": "Jane Doe",
  "email": "jane@example.com"
}
```

### Register attendee for specific date

```bash
POST https://my.demio.com/api/v1/event/register

Headers:
  Api-Key: {API_KEY}
  Api-Secret: {API_SECRET}
  Content-Type: application/json

{
  "id": 12345,
  "date_id": 67890,
  "name": "Jane Doe",
  "email": "jane@example.com"
}
```

### Get participants for 事件 date

```bash
GET https://my.demio.com/api/v1/date/{date_id}/participants

Headers:
  Api-Key: {API_KEY}
  Api-Secret: {API_SECRET}
```

## API 模式

Demio uses a straightforward REST API:
- All requests require both `Api-Key` and `Api-Secret` 请求头
- Responses are JSON objects
- Registration returns a `join_link` URL for the attendee
- Events have multiple "dates" (sessions), each with a unique `date_id`

## 核心指标

### 事件 指标
- `id` - 事件 ID
- `name` - 事件 name
- `date_id` - Session/date identifier
- `status` - 事件 status (upcoming, past, active)
- `type` - 事件 类型 (live, automated, on-demand)
- `registration_url` - Public registration page URL

### Participant 指标
- `name` - Participant name
- `email` - Participant email
- `status` - Attendance status (registered, attended, missed)
- `attended_minutes` - Duration of attendance
- `join_link` - Unique join URL for the participant

## Parameters

### 事件 List Filters
- `type` - Filter by 事件 类型: `upcoming`, `past`, `all`

### Registration Fields
- `id` - 事件 ID (required)
- `name` - Registrant name (required)
- `email` - Registrant email (required)
- `date_id` - Specific session date ID (optional)
- `ref_url` - Referral URL for 跟踪 (optional)

### Custom Fields
- Custom fields are supported via their UID (not 展示 name)
- Check your 事件 settings for available custom field UIDs

## 适用场景

- Automating webinar registration from landing pages or forms
- Syncing webinar attendee data with CRM
- Building custom registration flows for webinars
- 跟踪 webinar attendance and engagement
- Triggering follow-up sequences based on attendance status
- Managing multiple webinar sessions programmatically

## 速率限制

- **180 requests per minute** (3 per second)
- **Free Trial**: 100 API calls per day
- **Paid Plans**: 5,000 API calls per day (reset at 00:00 UTC)
- Contact Demio to request higher daily limits
- Exceeding limits returns an error response

## 相关技能

- webinar-营销
- lead-generation
- 事件-营销
- content-strategy
- lifecycle-营销
