# PartnerStack

Partner and affiliate program management 平台 for SaaS companies with deal 跟踪, rewards, and multi-tier partnerships.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Vendor API v2 for partnerships, deals, 客户, transactions |
| MCP | - | 不可用 |
| CLI | ✓ | [partnerstack.js](../clis/partnerstack.js) |
| SDK | - | No official SDK; REST API with Basic Auth |

## 认证方式

- **类型**: Basic Auth (Vendor API)
- **请求头**: `Authorization: Basic {base64(public_key:secret_key)}`
- **Get credentials**: Vendor dashboard > Settings > Integrations > PartnerStack API Keys
- **Note**: Separate Test and Production API keys. Test transactions can only be added to 客户 created with Test keys.

## 常见代理操作

### List partnerships

```bash
GET https://api.partnerstack.com/api/v2/partnerships?limit=25

Authorization: Basic {base64(public_key:secret_key)}
```

### Create a partnership

```bash
POST https://api.partnerstack.com/api/v2/partnerships

{
  "email": "partner@example.com",
  "group_key": "affiliates",
  "first_name": "Jane",
  "last_name": "Smith"
}
```

### List 客户

```bash
GET https://api.partnerstack.com/api/v2/customers?limit=25
```

### Create a 客户 (attribute to partner)

```bash
POST https://api.partnerstack.com/api/v2/customers

{
  "email": "customer@example.com",
  "partner_key": "prtnr_abc123",
  "name": "John Doe"
}
```

### Record a transaction

```bash
POST https://api.partnerstack.com/api/v2/transactions

{
  "customer_key": "cust_abc123",
  "amount": 9900,
  "currency": "USD",
  "product_key": "pro_plan"
}
```

### List deals

```bash
GET https://api.partnerstack.com/api/v2/deals?limit=25
```

### Create a deal

```bash
POST https://api.partnerstack.com/api/v2/deals

{
  "partner_key": "prtnr_abc123",
  "name": "Enterprise Opportunity",
  "amount": 50000,
  "stage": "qualified"
}
```

### Record an action (事件-based rewards)

```bash
POST https://api.partnerstack.com/api/v2/actions

{
  "customer_key": "cust_abc123",
  "key": "signup_completed",
  "value": 1
}
```

### Create a reward

```bash
POST https://api.partnerstack.com/api/v2/rewards

{
  "partner_key": "prtnr_abc123",
  "amount": 5000,
  "description": "Bonus for Q1 performance"
}
```

### List leads

```bash
GET https://api.partnerstack.com/api/v2/leads?limit=25
```

### Create a lead

```bash
POST https://api.partnerstack.com/api/v2/leads

{
  "partner_key": "prtnr_abc123",
  "email": "lead@company.com",
  "name": "Potential Customer",
  "company": "Acme Corp"
}
```

### List partner groups

```bash
GET https://api.partnerstack.com/api/v2/groups
```

### Manage webhooks

```bash
POST https://api.partnerstack.com/api/v2/webhooks

{
  "target": "https://example.com/webhooks/partnerstack",
  "events": ["deal.created", "transaction.created", "customer.created"]
}
```

## API Pattern

PartnerStack uses cursor-based pagination. List responses include `has_more` and item keys for `starting_after` / `ending_before` parameters.

All responses follow the format:
```json
{
  "data": { ... },
  "message": "...",
  "status": "2xx"
}
```

## 核心指标

### Partnership 指标
- `partner_key` - Unique partner identifier
- `group` - Partner tier/group
- `status` - active, pending, archived
- `created_at` - Partnership start date

### Transaction 指标
- `amount` - Transaction value in cents
- `currency` - Currency code
- `product_key` - Associated 产品
- `customer_key` - Associated 客户

### Deal 指标
- `amount` - Deal value
- `stage` - Deal pipeline stage
- `status` - open, won, lost

### Reward 指标
- `amount` - Reward amount in cents
- `status` - pending, approved, paid

## Parameters

### Pagination Parameters
- `limit` - Items per page (1-250, default: 10)
- `starting_after` - Cursor for next page (item key)
- `ending_before` - Cursor for previous page (item key)
- `order_by` - Sort field, prefix with `-` for descending

### 常见 Filters
- `include_archived` - Include archived records
- `has_sub_id` - Filter by sub ID presence

## 适用场景

- Managing SaaS affiliate and referral programs
- 跟踪 partner-driven revenue and attributions
- Automating partner onboarding and rewards
- Deal registration and pipeline 跟踪
- Multi-tier partnership programs (affiliates, resellers, agencies)
- 事件-based reward triggers (signups, upgrades, etc.)

## 速率限制

- Not explicitly documented
- Use reasonable request rates; implement exponential backoff on 429 responses

## 相关技能

- referral-program
- affiliate-营销
- partner-enablement
- saas-指标
- launch-sequence
