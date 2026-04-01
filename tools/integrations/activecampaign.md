# ActiveCampaign

Email 营销 automation 平台 with CRM, contacts, deals pipeline, tags, automations, and 广告活动 management.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API v3 for contacts, deals, automations, 广告活动, tags |
| MCP | - | 不可用 |
| CLI | ✓ | [activecampaign.js](../clis/activecampaign.js) |
| SDK | ✓ | Python, PHP, Node.js, Ruby |

## 认证方式

- **类型**: API Token
- **请求头**: `Api-Token: {api_token}`
- **Base URL**: `https://{yourAccountName}.api-us1.com/api/3`
- **Get key**: Settings > Developer tab in your ActiveCampaign 账户
- **Note**: Each user has a unique API key. Base URL is 账户-specific (found in Settings > Developer).

## 常见代理操作

### Get current 用户

```bash
GET https://{account}.api-us1.com/api/3/users/me
```

### List contacts

```bash
GET https://{account}.api-us1.com/api/3/contacts?limit=20&offset=0

# Search by 邮件
GET https://{account}.api-us1.com/api/3/contacts?email=user@example.com

# Search by name
GET https://{account}.api-us1.com/api/3/contacts?search=Jane
```

### Create contact

```bash
POST https://{account}.api-us1.com/api/3/contacts

{
  "contact": {
    "email": "user@example.com",
    "firstName": "Jane",
    "lastName": "Doe",
    "phone": "+15551234567"
  }
}
```

### Update contact

```bash
PUT https://{account}.api-us1.com/api/3/contacts/{contactId}

{
  "contact": {
    "firstName": "Updated",
    "lastName": "Name"
  }
}
```

### Sync contact (create or update)

```bash
POST https://{account}.api-us1.com/api/3/contact/sync

{
  "contact": {
    "email": "user@example.com",
    "firstName": "Jane",
    "lastName": "Doe"
  }
}
```

### Delete contact

```bash
DELETE https://{account}.api-us1.com/api/3/contacts/{contactId}
```

### List all lists

```bash
GET https://{account}.api-us1.com/api/3/lists?limit=20&offset=0
```

### Create list

```bash
POST https://{account}.api-us1.com/api/3/lists

{
  "list": {
    "name": "Newsletter",
    "stringid": "newsletter",
    "sender_url": "https://example.com",
    "sender_reminder": "You signed up for our newsletter."
  }
}
```

### Subscribe contact to list

```bash
POST https://{account}.api-us1.com/api/3/contactLists

{
  "contactList": {
    "list": "1",
    "contact": "1",
    "status": 1
  }
}
```

### Unsubscribe contact from list

```bash
POST https://{account}.api-us1.com/api/3/contactLists

{
  "contactList": {
    "list": "1",
    "contact": "1",
    "status": 2
  }
}
```

### 列出广告活动

```bash
GET https://{account}.api-us1.com/api/3/campaigns?limit=20&offset=0
```

### List deals

```bash
GET https://{account}.api-us1.com/api/3/deals?limit=20&offset=0

# Filter by pipeline stage
GET https://{account}.api-us1.com/api/3/deals?filters[stage]=1
```

### Create deal

```bash
POST https://{account}.api-us1.com/api/3/deals

{
  "deal": {
    "title": "New Enterprise Deal",
    "value": 50000,
    "currency": "usd",
    "group": "1",
    "stage": "1",
    "owner": "1",
    "contact": "1"
  }
}
```

### Update deal

```bash
PUT https://{account}.api-us1.com/api/3/deals/{dealId}

{
  "deal": {
    "stage": "2",
    "value": 75000
  }
}
```

### List automations

```bash
GET https://{account}.api-us1.com/api/3/automations?limit=20&offset=0
```

### Add contact to automation

```bash
POST https://{account}.api-us1.com/api/3/contactAutomations

{
  "contactAutomation": {
    "contact": "1",
    "automation": "1"
  }
}
```

### List tags

```bash
GET https://{account}.api-us1.com/api/3/tags?limit=20&offset=0
```

### Create tag

```bash
POST https://{account}.api-us1.com/api/3/tags

{
  "tag": {
    "tag": "VIP Customer",
    "tagType": "contact"
  }
}
```

### Add tag to contact

```bash
POST https://{account}.api-us1.com/api/3/contactTags

{
  "contactTag": {
    "contact": "1",
    "tag": "1"
  }
}
```

### List pipelines (deal groups)

```bash
GET https://{account}.api-us1.com/api/3/dealGroups?limit=20&offset=0
```

### List webhooks

```bash
GET https://{account}.api-us1.com/api/3/webhooks?limit=20&offset=0
```

### Create webhook

```bash
POST https://{account}.api-us1.com/api/3/webhooks

{
  "webhook": {
    "name": "Contact Updated",
    "url": "https://example.com/webhook",
    "events": ["subscribe", "unsubscribe"],
    "sources": ["public", "admin", "api", "system"]
  }
}
```

## API 模式

ActiveCampaign uses REST with resource wrapping (e.g., `{ "contact": {...} }`). Responses include the resource object plus metadata. Related resources are managed via junction endpoints (e.g., `/contactLists`, `/contactTags`, `/contactAutomations`). The base URL is 账户-specific. Pagination uses `limit` and `offset` parameters.

## 核心指标

### Contact Fields
- `email` - Email address
- `firstName`, `lastName` - Name fields
- `phone` - Phone number
- `cdate` - Creation date
- `udate` - Last updated date
- `deals` - Related deals count

### Deal Fields
- `title` - Deal name
- `value` - Deal value in cents
- `currency` - Currency code
- `stage` - Pipeline stage ID
- `group` - Pipeline (deal group) ID
- `owner` - Assigned user ID
- `status` - 0 (open), 1 (won), 2 (lost)

### 广告活动 指标
- `sends` - Total sends
- `opens` - Opens count
- `clicks` - 点击 count
- `uniqueopens` - Unique opens
- `uniquelinks` - Unique 点击

## Parameters

### Contact List 状态
- `1` - Subscribed (active)
- `2` - Unsubscribed

### Deal 状态
- `0` - Open
- `1` - Won
- `2` - Lost

### Tag Types
- `contact` - Contact tags
- `deal` - Deal tags

### 常见 Query Parameters
- `limit` - Results per page (default 20)
- `offset` - Skip N results
- `search` - Text 搜索
- `email` - Filter contacts by email
- `filters[stage]` - Filter deals by stage
- `filters[owner]` - Filter deals by owner

## 适用场景

- 营销 automation with complex conditional 工作流
- CRM with deal pipeline 管理
- Contact management with tagging and segmentation
- Email 广告活动 creation and 跟踪
- Triggering automations based on external events
- B2B sales pipeline 跟踪 integrated with 营销

## 速率限制

- 5 requests per second per 账户
- Rate limit applies across all API users on the same 账户
- 429 responses include `Retry-After` 请求头

## 相关技能

- email-sequence
- lifecycle-营销
- crm-integration
- sales-pipeline
- 营销-automation
