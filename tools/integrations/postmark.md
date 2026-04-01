# Postmark

Transactional email delivery service with fast delivery, templates, bounce management, and detailed 分析.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for email sending, templates, bounces, stats |
| MCP | - | 不可用 |
| CLI | ✓ | [postmark.js](../clis/postmark.js) |
| SDK | ✓ | Node.js, Ruby, Python, PHP, Java, .NET, Go |

## 认证方式

- **类型**: Server Token (or 账户 Token for 账户-level ops)
- **请求头**: `X-Postmark-Server-Token: {server_token}` (server-level)
- **请求头**: `X-Postmark-Account-Token: {account_token}` (账户-level)
- **Get key**: API Tokens tab at https://账户.postmarkapp.com/servers
- **Note**: Server tokens are per-server; 账户 tokens apply across all servers

## 常见代理操作

### Send single email

```bash
POST https://api.postmarkapp.com/email

{
  "From": "sender@example.com",
  "To": "recipient@example.com",
  "Subject": "Welcome!",
  "HtmlBody": "<html><body><p>Hello!</p></body></html>",
  "TextBody": "Hello!",
  "MessageStream": "outbound",
  "TrackOpens": true,
  "TrackLinks": "HtmlAndText"
}
```

### Send with template

```bash
POST https://api.postmarkapp.com/email/withTemplate

{
  "From": "sender@example.com",
  "To": "recipient@example.com",
  "TemplateId": 12345,
  "TemplateModel": {
    "name": "Jane",
    "action_url": "https://example.com/verify"
  },
  "MessageStream": "outbound"
}
```

### Send batch emails

```bash
POST https://api.postmarkapp.com/email/batch

[
  {
    "From": "sender@example.com",
    "To": "user1@example.com",
    "Subject": "Notification",
    "TextBody": "Hello user 1"
  },
  {
    "From": "sender@example.com",
    "To": "user2@example.com",
    "Subject": "Notification",
    "TextBody": "Hello user 2"
  }
]
```

### List templates

```bash
GET https://api.postmarkapp.com/templates?Count=100&Offset=0
```

### Get template

```bash
GET https://api.postmarkapp.com/templates/{templateIdOrAlias}
```

### Create template

```bash
POST https://api.postmarkapp.com/templates

{
  "Name": "Welcome Email",
  "Alias": "welcome",
  "Subject": "Welcome {{name}}!",
  "HtmlBody": "<html><body><p>Hello {{name}}</p></body></html>",
  "TextBody": "Hello {{name}}"
}
```

### Get delivery stats

```bash
GET https://api.postmarkapp.com/deliverystats
```

### List bounces

```bash
GET https://api.postmarkapp.com/bounces?count=50&offset=0&type=HardBounce
```

### Activate bounce (reactivate recipient)

```bash
PUT https://api.postmarkapp.com/bounces/{bounceId}/activate
```

### 搜索 outbound messages

```bash
GET https://api.postmarkapp.com/messages/outbound?count=50&offset=0&recipient=user@example.com
```

### Get outbound stats 概览

```bash
GET https://api.postmarkapp.com/stats/outbound?fromdate=2025-01-01&todate=2025-01-31
```

### Get open stats

```bash
GET https://api.postmarkapp.com/stats/outbound/opens?fromdate=2025-01-01&todate=2025-01-31
```

### Get click stats

```bash
GET https://api.postmarkapp.com/stats/outbound/clicks?fromdate=2025-01-01&todate=2025-01-31
```

### Get server info

```bash
GET https://api.postmarkapp.com/server
```

### List suppressions

```bash
GET https://api.postmarkapp.com/message-streams/outbound/suppressions/dump
```

### Create suppression

```bash
POST https://api.postmarkapp.com/message-streams/outbound/suppressions

{
  "Suppressions": [
    { "EmailAddress": "user@example.com" }
  ]
}
```

## API Pattern

Postmark uses simple REST endpoints with PascalCase field names in request/response bodies. 认证 is via custom 请求头 rather than Authorization. Pagination uses `Count` and `Offset` parameters. Email sending is synchronous with immediate delivery confirmation.

## 核心指标

### Delivery 指标
- `Sent` - Total emails sent
- `Bounced` - Bounce count by 类型 (hard, soft, transient)
- `SpamComplaints` - Spam complaint count
- `Opens` - Open count and unique opens
- `Clicks` - Click count and unique 点击

### Bounce Types
- `HardBounce` - Permanent delivery failure
- `SoftBounce` - Temporary delivery failure
- `Transient` - Temporary issue (retry)
- `SpamNotification` - Marked as spam

### Message Fields
- `MessageID` - Unique message identifier
- `SubmittedAt` - Submission timestamp
- `Status` - Delivery status
- `Recipients` - Recipient list

## Parameters

### Email Parameters
- `From` - Sender address (must be verified)
- `To` - Recipient (comma-separated for multiple)
- `Subject` - Email subject
- `HtmlBody` / `TextBody` - Email content
- `MessageStream` - outbound (transactional) or broadcast
- `TrackOpens` - Enable open 跟踪 (boolean)
- `TrackLinks` - None, HtmlAndText, HtmlOnly, TextOnly
- `Tag` - Custom tag for categorization

### Stats Parameters
- `fromdate` - Start date (YYYY-MM-DD)
- `todate` - End date (YYYY-MM-DD)
- `tag` - Filter by tag

## 适用场景

- Transactional emails (password resets, order confirmations, notifications)
- Template-based email sending with dynamic variables
- Monitoring email deliverability and bounce rates
- 跟踪 email engagement (opens, 点击)
- Managing email suppressions and bounces
- High-reliability email delivery with fast 表现

## 速率限制

- 500 messages per batch request
- 10 MB max per single message (including attachments)
- 50 MB max per batch request
- API 速率限制 vary by plan

## 相关技能

- email-sequence
- transactional-email
- email-deliverability
- onboarding-email
