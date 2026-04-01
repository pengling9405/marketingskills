# Close

Sales CRM for SMBs with built-in calling, email, and pipeline management designed for high-velocity sales teams.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Leads, Contacts, Opportunities, Activities, Tasks |
| MCP | - | 不可用 |
| CLI | ✓ | [close.js](../clis/close.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: Basic Auth
- **请求头**: `Authorization: Basic {base64(api_key + ':')}`
- **Get key**: Settings > API Keys at https://app.close.com

## 常见代理操作

### List Leads

```bash
GET https://api.close.com/api/v1/lead/

Authorization: Basic {base64(api_key + ':')}
```

### 搜索 Leads

```bash
GET https://api.close.com/api/v1/lead/?query=company_name

Authorization: Basic {base64(api_key + ':')}
```

### Create Lead

```bash
POST https://api.close.com/api/v1/lead/

{
  "name": "Acme Corp",
  "url": "https://acme.com",
  "description": "Enterprise prospect"
}
```

### Get Contact

```bash
GET https://api.close.com/api/v1/contact/{contact_id}/

Authorization: Basic {base64(api_key + ':')}
```

### Create Contact

```bash
POST https://api.close.com/api/v1/contact/

{
  "lead_id": "lead_xxx",
  "name": "Jane Smith",
  "emails": [{ "email": "jane@acme.com", "type": "office" }],
  "phones": [{ "phone": "+15551234567", "type": "office" }]
}
```

### Create Opportunity

```bash
POST https://api.close.com/api/v1/opportunity/

{
  "lead_id": "lead_xxx",
  "value": 50000,
  "status_type": "active"
}
```

### List Activities

```bash
GET https://api.close.com/api/v1/activity/?lead_id=lead_xxx

Authorization: Basic {base64(api_key + ':')}
```

### Create Task

```bash
POST https://api.close.com/api/v1/task/

{
  "lead_id": "lead_xxx",
  "text": "Follow up on demo request",
  "_type": "lead",
  "date": "2026-03-10"
}
```

## 核心指标

### Lead Data
- `id` - Lead ID
- `display_name` - Lead name
- `url` - Website URL
- `description` - Lead description
- `status_id` - Pipeline status
- `contacts` - Associated contacts
- `opportunities` - Associated opportunities
- `tasks` - Associated tasks

### Contact Data
- `id` - Contact ID
- `lead_id` - Parent lead
- `name` - Full name
- `title` - Job title
- `emails` - Email addresses array
- `phones` - Phone numbers array

### Opportunity Data
- `id` - Opportunity ID
- `lead_id` - Parent lead
- `value` - Value in cents
- `status_type` - active, won, or lost
- `confidence` - Win probability (0-100)
- `date_won` - Close date

### Task Data
- `id` - Task ID
- `lead_id` - Parent lead
- `text` - Task description
- `assigned_to` - Assigned user ID
- `date` - Due date
- `is_complete` - Completion status

## Parameters

### Leads
- `query` - 搜索 query string
- `_skip` - Number of results to skip (pagination)
- `_limit` - Max results to return (default: 100)
- `_fields` - Comma-separated fields to return

### Contacts
- `lead_id` - Filter by parent lead
- `_skip` - Pagination offset
- `_limit` - Max results

### Opportunities
- `lead_id` - Filter by parent lead
- `status` - Filter by status 类型 (active, won, lost)
- `_skip` - Pagination offset
- `_limit` - Max results

### Activities
- `lead_id` - Filter by lead
- `_type__type` - Filter by 类型 (Email, Call, Note, SMS, Meeting)
- `date_created__gt` - After date
- `date_created__lt` - Before date

### Tasks
- `assigned_to` - Filter by user ID
- `is_complete` - Filter by completion (true/false)
- `lead_id` - Filter by lead
- `_type` - Task 类型 (lead)

## 适用场景

- Managing SMB sales pipelines with high-touch outreach
- 跟踪 sales activities (calls, emails, meetings) per lead
- Creating and managing tasks for sales follow-ups
- Opportunity 跟踪 and revenue forecasting
- Building automated outreach 工作流
- Sales team 表现 reporting

## 速率限制

- 速率限制 based on organization plan
- Standard: ~100 requests/minute
- Responses include `ratelimit-limit` and `ratelimit-remaining` 请求头
- 429 responses include `Retry-After` 请求头

## 相关技能

- revops
- sales-enablement
- cold-email
