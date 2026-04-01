# Brevo

All-in-one 营销 平台 (formerly Sendinblue) for email, SMS, and WhatsApp with contacts, 广告活动, and transactional messaging.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API v3 for contacts, 广告活动, transactional email/SMS |
| MCP | - | 不可用 |
| CLI | ✓ | [brevo.js](../clis/brevo.js) |
| SDK | ✓ | Node.js, Python, PHP, Ruby, Java, C#, Go |

## 认证方式

- **类型**: API Key
- **请求头**: `api-key: {api_key}`
- **Get key**: SMTP & API settings at https://app.brevo.com/settings/keys/API
- **Note**: API key is only shown once on creation; store securely. Formerly used `api.sendinblue.com` base URL.

## 常见代理操作

### 获取账户信息

```bash
GET https://api.brevo.com/v3/account
```

### List contacts

```bash
GET https://api.brevo.com/v3/contacts?limit=50&offset=0
```

### Get contact by email

```bash
GET https://api.brevo.com/v3/contacts/user@example.com
```

### Create contact

```bash
POST https://api.brevo.com/v3/contacts

{
  "email": "user@example.com",
  "attributes": {
    "FIRSTNAME": "Jane",
    "LASTNAME": "Doe"
  },
  "listIds": [1, 2]
}
```

### Update contact

```bash
PUT https://api.brevo.com/v3/contacts/user@example.com

{
  "attributes": {
    "FIRSTNAME": "Updated"
  },
  "listIds": [3]
}
```

### Delete contact

```bash
DELETE https://api.brevo.com/v3/contacts/user@example.com
```

### Import contacts

```bash
POST https://api.brevo.com/v3/contacts/import

{
  "jsonBody": [
    { "email": "user1@example.com" },
    { "email": "user2@example.com" }
  ],
  "listIds": [1]
}
```

### List contact lists

```bash
GET https://api.brevo.com/v3/contacts/lists?limit=50&offset=0
```

### Create list

```bash
POST https://api.brevo.com/v3/contacts/lists

{
  "name": "Newsletter Subscribers",
  "folderId": 1
}
```

### Add contacts to list

```bash
POST https://api.brevo.com/v3/contacts/lists/{listId}/contacts/add

{
  "emails": ["user1@example.com", "user2@example.com"]
}
```

### Remove contacts from list

```bash
POST https://api.brevo.com/v3/contacts/lists/{listId}/contacts/remove

{
  "emails": ["user1@example.com"]
}
```

### Send transactional email

```bash
POST https://api.brevo.com/v3/smtp/email

{
  "sender": {
    "name": "My App",
    "email": "noreply@example.com"
  },
  "to": [
    { "email": "user@example.com", "name": "Jane Doe" }
  ],
  "subject": "Order Confirmation",
  "htmlContent": "<html><body><p>Your order is confirmed.</p></body></html>"
}
```

### List email 广告活动

```bash
GET https://api.brevo.com/v3/emailCampaigns?limit=50&offset=0&type=classic&status=sent
```

### Create email 广告活动

```bash
POST https://api.brevo.com/v3/emailCampaigns

{
  "name": "January Newsletter",
  "subject": "Monthly Update",
  "sender": { "name": "My Brand", "email": "news@example.com" },
  "htmlContent": "<html><body><p>Newsletter content</p></body></html>",
  "recipients": { "listIds": [1, 2] }
}
```

### Send 广告活动 immediately

```bash
POST https://api.brevo.com/v3/emailCampaigns/{campaignId}/sendNow
```

### Send test email for 广告活动

```bash
POST https://api.brevo.com/v3/emailCampaigns/{campaignId}/sendTest

{
  "emailTo": ["test@example.com"]
}
```

### Send transactional SMS

```bash
POST https://api.brevo.com/v3/transactionalSMS/sms

{
  "sender": "MyApp",
  "recipient": "+15551234567",
  "content": "Your verification code is 123456",
  "type": "transactional"
}
```

### List SMS 广告活动

```bash
GET https://api.brevo.com/v3/smsCampaigns?limit=50&offset=0
```

### List senders

```bash
GET https://api.brevo.com/v3/senders
```

## API Pattern

Brevo uses standard REST with offset-based pagination (`limit` and `offset` parameters). Contact attributes use uppercase field names (FIRSTNAME, LASTNAME). Lists are nested under the contacts resource path. Transactional email uses the `/smtp/email` endpoint despite being REST-based.

## 核心指标

### Contact Fields
- `email` - Email address
- `attributes` - Custom attributes (FIRSTNAME, LASTNAME, SMS, etc.)
- `listIds` - Associated list IDs
- `emailBlacklisted` - Email opt-out status
- `smsBlacklisted` - SMS opt-out status
- `statistics` - Engagement stats (with expand)

### 广告活动 指标
- `sent` - Total sends
- `delivered` - Successful deliveries
- `openRate` - Open percentage
- `clickRate` - Click percentage
- `unsubscribed` - Unsubscribe count
- `hardBounces`, `softBounces` - Bounce counts

### Transactional Email Response
- `messageId` - Unique message identifier for 跟踪

## Parameters

### Contact Parameters
- `email` - Contact email address
- `attributes` - Key-value object of custom attributes
- `listIds` - Array of list IDs to subscribe to
- `unlinkListIds` - Array of list IDs to unsubscribe from

### 广告活动 Parameters
- `name` - 广告活动 name
- `subject` - Email subject line
- `sender` - Object with `name` and `email`
- `htmlContent` / `textContent` - Email body
- `recipients` - Object with `listIds` array
- `type` - classic or trigger

## 适用场景

- Multi-channel 营销 (email + SMS + WhatsApp)
- Transactional email sending with 跟踪
- Managing contacts and segmented lists
- Creating and scheduling email 广告活动
- SMS notifications and 营销
- Affordable all-in-one 营销 automation

## 速率限制

- API 速率限制 depend on plan (free tier: limited sends/day)
- Transactional email: varies by plan
- Contact imports: batch processing with async status
- Rate limit 请求头 returned with responses

## 相关技能

- email-sequence
- sms-营销
- transactional-email
- lifecycle-营销
- contact-management
