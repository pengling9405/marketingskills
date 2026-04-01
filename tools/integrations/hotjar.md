# Hotjar

Behavior 分析 平台 with heatmaps, session recordings, and surveys for understanding user experience.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Surveys, Responses, Sites, Heatmaps, Recordings |
| MCP | - | 不可用 |
| CLI | ✓ | [hotjar.js](../clis/hotjar.js) |
| SDK | ✓ | JavaScript 跟踪 snippet, Identify API, Events API |

## 认证方式

- **类型**: OAuth 2.0 Client Credentials
- **Token endpoint**: `POST https://api.hotjar.io/v1/oauth/token`
- **请求头**: `Authorization: Bearer {access_token}`
- **Get credentials**: Hotjar Dashboard > Integrations > API
- **Token expiry**: 3600 seconds (1 hour)

### Token Request

```bash
POST https://api.hotjar.io/v1/oauth/token
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials&client_id={client_id}&client_secret={client_secret}
```

### Token Response

```json
{
  "access_token": "<token>",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

## 常见代理操作

### List Sites

```bash
GET https://api.hotjar.io/v1/sites

Authorization: Bearer {access_token}
```

### List Surveys

```bash
GET https://api.hotjar.io/v1/sites/{site_id}/surveys

Authorization: Bearer {access_token}
```

### Get Survey Responses

```bash
GET https://api.hotjar.io/v1/sites/{site_id}/surveys/{survey_id}/responses?limit=100

Authorization: Bearer {access_token}
```

Supports cursor-based pagination with `cursor` and `limit` parameters.

### List Heatmaps

```bash
GET https://api.hotjar.io/v1/sites/{site_id}/heatmaps

Authorization: Bearer {access_token}
```

### List Recordings

```bash
GET https://api.hotjar.io/v1/sites/{site_id}/recordings

Authorization: Bearer {access_token}
```

### List Forms

```bash
GET https://api.hotjar.io/v1/sites/{site_id}/forms

Authorization: Bearer {access_token}
```

## 核心指标

### Survey Response Data
- `response_id` - Unique response identifier
- `answers` - Array of question/answer pairs
- `created_at` - Response timestamp
- `device_type` - Desktop, mobile, tablet

### Heatmap Data
- `url` - Page URL
- `click_count` - Total 点击 tracked
- `visitors` - Unique visitors
- `created_at` - Heatmap creation date

### Recording Data
- `recording_id` - Unique recording ID
- `duration` - Session duration
- `pages_visited` - Pages in session
- `device` - Device information

## Parameters

### Survey Responses
- `limit` - Results per page (default: 100)
- `cursor` - Pagination cursor from previous response
- `sort` - Sort order (default: created_at desc)

### Recordings
- `limit` - Results per page
- `cursor` - Pagination cursor
- `date_from` - Start date filter
- `date_to` - End date filter

## 适用场景

- Analyzing user behavior patterns on landing pages
- Collecting qualitative feedback via on-site surveys
- Identifying UX issues through session recordings
- Understanding scroll depth and engagement via heatmaps
- Validating CRO hypotheses with user behavior data
- Form abandonment 分析

## 速率限制

- 3000 requests/minute (50 per second)
- Rate limited by 来源 IP address
- Cursor-based pagination for large result sets

## 相关技能

- page-cro
- ab-test-setup
- 分析-跟踪
- ux-audit
- landing-page
