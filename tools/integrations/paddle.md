# Paddle

SaaS billing and payments 平台 with built-in tax 遵循率, acting as merchant of record for global sales.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for products, prices, subscriptions, transactions |
| MCP | - | 不可用 |
| CLI | ✓ | [paddle.js](../clis/paddle.js) |
| SDK | ✓ | Node.js, Python, PHP, Go |

## 认证方式

- **类型**: Bearer Token
- **请求头**: `Authorization: Bearer {api_key}`
- **Get key**: Paddle dashboard > Developer Tools > 认证
- **Production URL**: `https://api.paddle.com`
- **Sandbox URL**: `https://sandbox-api.paddle.com`
- **Note**: Version specified via 请求头, not path. Set `PADDLE_SANDBOX=true` env var for sandbox.

## 常见代理操作

### List products

```bash
GET https://api.paddle.com/products
```

### Create a 产品

```bash
POST https://api.paddle.com/products

{
  "name": "Pro Plan",
  "tax_category": "standard",
  "description": "Professional tier subscription"
}
```

### Create a price for a 产品

```bash
POST https://api.paddle.com/prices

{
  "product_id": "pro_01abc...",
  "description": "Monthly Pro",
  "unit_price": {
    "amount": "2999",
    "currency_code": "USD"
  },
  "billing_cycle": {
    "interval": "month",
    "frequency": 1
  }
}
```

### List 客户

```bash
GET https://api.paddle.com/customers
```

### Create a 客户

```bash
POST https://api.paddle.com/customers

{
  "email": "customer@example.com",
  "name": "Jane Smith"
}
```

### List subscriptions

```bash
GET https://api.paddle.com/subscriptions?status=active
```

### Get subscription details

```bash
GET https://api.paddle.com/subscriptions/{subscription_id}
```

### Cancel a subscription

```bash
POST https://api.paddle.com/subscriptions/{subscription_id}/cancel

{
  "effective_from": "next_billing_period"
}
```

### Pause a subscription

```bash
POST https://api.paddle.com/subscriptions/{subscription_id}/pause
```

### List transactions

```bash
GET https://api.paddle.com/transactions
```

### Create a discount

```bash
POST https://api.paddle.com/discounts

{
  "amount": "20",
  "type": "percentage",
  "description": "20% off first month",
  "code": "WELCOME20"
}
```

### Create a refund adjustment

```bash
POST https://api.paddle.com/adjustments

{
  "transaction_id": "txn_01abc...",
  "action": "refund",
  "reason": "Customer requested refund",
  "items": [{"item_id": "txnitm_01abc...", "type": "full"}]
}
```

### List events

```bash
GET https://api.paddle.com/events
```

### List 事件 types

```bash
GET https://api.paddle.com/event-types
```

## 核心指标

### Transaction 指标
- `totals.total` - Total amount charged
- `totals.tax` - Tax amount
- `totals.subtotal` - Amount before tax
- `totals.discount` - Discount applied
- `currency_code` - Transaction currency

### Subscription 指标
- `status` - active, canceled, paused, past_due, trialing
- `current_billing_period` - Current period start/end
- `next_billed_at` - Next billing date
- `scheduled_change` - Pending changes (cancellation, plan change)

### 产品/Price 指标
- `unit_price.amount` - Price in lowest denomination
- `billing_cycle` - Interval and frequency
- `trial_period` - Trial duration if set

## Parameters

### List Filtering
- `status` - Filter by status (e.g., active, archived)
- `after` - Cursor for pagination
- `per_page` - Results per page (default: 50)
- `order_by` - Sort field and direction

### Subscription Cancel Options
- `effective_from` - `immediately` or `next_billing_period`

### Price Billing Cycle
- `interval` - `day`, `week`, `month`, `year`
- `frequency` - Number of intervals between billings

### Tax Categories
- `standard` - Standard tax rate
- `digital-goods` - Digital goods tax rate
- `saas` - SaaS-specific tax rate

## 适用场景

- Managing SaaS subscription billing with tax 遵循率
- Creating products and pricing tiers
- Processing refunds and adjustments
- Handling subscription lifecycle (create, pause, cancel, resume)
- Global tax handling as merchant of record
- Discount and coupon management for promotions

## 速率限制

- 100 requests per minute
- Applies across all endpoints
- HTTP 429 returned when exceeded

## 相关技能

- pricing-page
- saas-指标
- churn-reduction
- launch-sequence
- monetization-strategy
