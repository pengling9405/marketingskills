# SendGrid

Email delivery 平台 for transactional and 营销 emails.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Mail Send API, 营销 API |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | Official libraries for most languages |

## 认证方式

- **类型**: API Key
- **请求头**: `Authorization: Bearer {api_key}`
- **Get key**: Settings > API Keys in SendGrid dashboard

## 常见代理操作

### Send 邮件

```bash
POST https://api.sendgrid.com/v3/mail/send

Authorization: Bearer {api_key}

{
  "personalizations": [{
    "to": [{"email": "user@example.com"}]
  }],
  "from": {"email": "hello@example.com"},
  "subject": "Welcome!",
  "content": [{
    "type": "text/html",
    "value": "<h1>Welcome!</h1>"
  }]
}
```

### Send with template

```bash
POST https://api.sendgrid.com/v3/mail/send

{
  "personalizations": [{
    "to": [{"email": "user@example.com"}],
    "dynamic_template_data": {
      "name": "John",
      "order_id": "12345"
    }
  }],
  "from": {"email": "hello@example.com"},
  "template_id": "d-xxx"
}
```

### Add contact to list

```bash
PUT https://api.sendgrid.com/v3/marketing/contacts

{
  "list_ids": ["list-id"],
  "contacts": [{
    "email": "user@example.com",
    "first_name": "John",
    "last_name": "Doe"
  }]
}
```

### 搜索 contacts

```bash
POST https://api.sendgrid.com/v3/marketing/contacts/search

{
  "query": "email LIKE 'user@%'"
}
```

### Get 邮件 statistics

```bash
GET https://api.sendgrid.com/v3/stats?start_date=2024-01-01&end_date=2024-01-31

Authorization: Bearer {api_key}
```

### Get bounces

```bash
GET https://api.sendgrid.com/v3/suppression/bounces

Authorization: Bearer {api_key}
```

### Get spam reports

```bash
GET https://api.sendgrid.com/v3/suppression/spam_reports

Authorization: Bearer {api_key}
```

### Validate 邮件

```bash
POST https://api.sendgrid.com/v3/validations/email

{
  "email": "user@example.com"
}
```

## Webhook Events

| 事件 | 说明 |
|-------|-------------|
| `processed` | Email accepted |
| `delivered` | Email delivered |
| `open` | Email opened |
| `click` | Link clicked |
| `bounce` | Hard/soft bounce |
| `dropped` | Email dropped |
| `spamreport` | Marked as spam |
| `unsubscribe` | Unsubscribed |

## Node.js SDK

```javascript
const sgMail = require('@sendgrid/mail');
sgMail.setApiKey('SG.xxx');

await sgMail.send({
  to: 'user@example.com',
  from: 'hello@example.com',
  subject: 'Welcome!',
  html: '<h1>Welcome!</h1>'
});
```

## 适用场景

- Transactional email at scale
- 营销 email 广告活动
- Email validation
- Deliverability 管理

## 速率限制

- Free: 100 emails/day
- Paid: Varies by plan (up to millions/month)

## 相关技能

- email-sequence
- 分析-跟踪
