# HubSpot

CRM 平台 for 营销, sales, and 客户 service.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for CRM, 营销, Sales |
| MCP | - | 不可用 |
| CLI | ✓ | `hs` CLI for local development |
| SDK | ✓ | Official client libraries |

## 认证方式

- **类型**: Private App Token or OAuth 2.0
- **请求头**: `Authorization: Bearer {access_token}`
- **获取令牌**： Settings > Integrations > Private Apps

## 常见代理操作

### Get contacts

```bash
GET https://api.hubapi.com/crm/v3/objects/contacts?limit=10

Authorization: Bearer {access_token}
```

### 搜索 contacts

```bash
POST https://api.hubapi.com/crm/v3/objects/contacts/search

{
  "filterGroups": [{
    "filters": [{
      "propertyName": "email",
      "operator": "EQ",
      "value": "user@example.com"
    }]
  }]
}
```

### Create contact

```bash
POST https://api.hubapi.com/crm/v3/objects/contacts

{
  "properties": {
    "email": "user@example.com",
    "firstname": "John",
    "lastname": "Doe",
    "company": "Example Inc"
  }
}
```

### Update contact

```bash
PATCH https://api.hubapi.com/crm/v3/objects/contacts/{contact_id}

{
  "properties": {
    "lifecyclestage": "customer"
  }
}
```

### Get deals

```bash
GET https://api.hubapi.com/crm/v3/objects/deals?limit=10&properties=dealname,amount,dealstage

Authorization: Bearer {access_token}
```

### Create deal

```bash
POST https://api.hubapi.com/crm/v3/objects/deals

{
  "properties": {
    "dealname": "New Deal",
    "amount": "10000",
    "dealstage": "appointmentscheduled",
    "pipeline": "default"
  }
}
```

### Associate contact with deal

```bash
PUT https://api.hubapi.com/crm/v3/objects/deals/{deal_id}/associations/contacts/{contact_id}/deal_to_contact
```

### Get form submissions

```bash
GET https://api.hubapi.com/form-integrations/v1/submissions/forms/{form_guid}

Authorization: Bearer {access_token}
```

### Get 营销 emails

```bash
GET https://api.hubapi.com/marketing/v3/emails?limit=10

Authorization: Bearer {access_token}
```

## CLI Commands

```bash
# Install
npm install -g @hubspot/cli

# Initialize project
hs init

# Upload files
hs upload src dest

# Watch for changes
hs watch src dest

# List portals
hs accounts list
```

## Key Objects

- **Contacts** - People in CRM
- **Companies** - Organizations
- **Deals** - Sales opportunities
- **Tickets** - Support tickets
- **Products** - Items for sale
- **Line Items** - Deal line items

## 常见 Properties

### Contact Properties
- `email` - Email address
- `firstname`, `lastname` - Name
- `lifecyclestage` - Funnel stage
- `hs_lead_status` - Lead status

### Deal Properties
- `dealname` - Deal name
- `amount` - Deal value
- `dealstage` - Pipeline stage
- `closedate` - Expected close

## 适用场景

- Managing contacts and leads
- 跟踪 sales deals
- 营销 automation
- Form submissions
- Email 广告活动
- 客户 service tickets

## 速率限制

- 100 requests per 10 seconds
- Higher limits on enterprise plans

## 相关技能

- email-sequence
- 分析-跟踪
- referral-program
