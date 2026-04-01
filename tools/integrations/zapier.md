# Zapier

工作流 automation 平台 connecting apps without code.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for Zaps, tasks, and webhooks |
| MCP | ✓ | 可用 via Zapier MCP server |
| CLI | - | 不可用 |
| SDK | - | API and webhooks only |

## 认证方式

- **类型**: API Key
- **请求头**: `X-API-Key: {api_key}`
- **Get key**: Settings > API in Zapier 账户

## 常见代理操作

### List Zaps

```bash
GET https://api.zapier.com/v1/zaps
```

### Get Zap details

```bash
GET https://api.zapier.com/v1/zaps/{zap_id}
```

### Turn Zap on/off

```bash
POST https://api.zapier.com/v1/zaps/{zap_id}/on
POST https://api.zapier.com/v1/zaps/{zap_id}/off
```

### Get task history

```bash
GET https://api.zapier.com/v1/zaps/{zap_id}/tasks
```

### Get profile info

```bash
GET https://api.zapier.com/v1/profiles/me
```

## Webhooks (Triggers)

### Catch Hook (receive data)

Create a "Webhooks by Zapier" trigger to receive data:

```bash
POST https://hooks.zapier.com/hooks/catch/{webhook_id}/

{
  "event": "user.created",
  "user_id": "123",
  "email": "user@example.com"
}
```

### Send data to Zapier

Most 常见: trigger a Zap from your app:

```bash
POST https://hooks.zapier.com/hooks/catch/{account_id}/{hook_id}/

{
  "name": "John Doe",
  "email": "john@example.com",
  "plan": "pro"
}
```

## 常见 营销 Automations

### Lead capture to CRM
```
Typeform → Zapier → HubSpot
```

### New 客户 notifications
```
Stripe (new customer) → Zapier → Slack
```

### Email sequence triggers
```
Form submission → Zapier → Customer.io
```

### 社会认同 automation
```
New review → Zapier → Twitter/Slack
```

### Referral 跟踪
```
New referral → Zapier → Spreadsheet + Slack
```

## Webhook Payload Structure

When sending to Zapier, structure data as flat JSON:

```json
{
  "customer_name": "John Doe",
  "customer_email": "john@example.com",
  "plan_name": "Pro",
  "plan_price": 99,
  "signup_date": "2024-01-15"
}
```

## 关键概念

- **Zap** - Automated 工作流
- **Trigger** - 事件 that starts a Zap
- **Action** - Task performed by Zap
- **Task** - Single action execution
- **Filter** - Conditional logic
- **Path** - Branching logic

## 适用场景

- Connecting 营销 tools without code
- Automating lead routing
- Syncing data between platforms
- Triggering notifications
- Building 营销 工作流

## 速率限制

- 100 requests per minute
- Task limits by plan tier

## 相关技能

- email-sequence
- 分析-跟踪
- referral-program
