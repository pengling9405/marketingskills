# Stripe

Payment processing, subscriptions, and billing for internet businesses.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Comprehensive REST API |
| MCP | ✓ | 可用 via Stripe MCP server |
| CLI | ✓ | `stripe` CLI for 测试 and webhooks |
| SDK | ✓ | Official SDKs for most languages |

## 认证方式

- **类型**: API Key
- **请求头**: `Authorization: Bearer sk_live_xxx` or `sk_test_xxx`
- **Keys**: Secret key (server), Publishable key (client)

## 常见代理操作

### List 客户

```bash
GET https://api.stripe.com/v1/customers?limit=10
```

### Get 客户 by 邮件

```bash
GET https://api.stripe.com/v1/customers?email=user@example.com
```

### Get subscription

```bash
GET https://api.stripe.com/v1/subscriptions/{subscription_id}
```

### List subscriptions for 客户

```bash
GET https://api.stripe.com/v1/subscriptions?customer={customer_id}
```

### Create checkout 会话

```bash
POST https://api.stripe.com/v1/checkout/sessions

customer={customer_id}
&line_items[0][price]={price_id}
&line_items[0][quantity]=1
&mode=subscription
&success_url=https://example.com/success
&cancel_url=https://example.com/cancel
```

### Create 客户 portal 会话

```bash
POST https://api.stripe.com/v1/billing_portal/sessions

customer={customer_id}
&return_url=https://example.com/account
```

### List recent invoices

```bash
GET https://api.stripe.com/v1/invoices?customer={customer_id}&limit=10
```

### Get payment intent

```bash
GET https://api.stripe.com/v1/payment_intents/{payment_intent_id}
```

## Webhook Events

Key events to handle:

| 事件 | When | Action |
|-------|------|--------|
| `checkout.session.completed` | Successful checkout | Provision access |
| `customer.subscription.created` | New subscription | Update user record |
| `customer.subscription.updated` | Plan change | Update entitlements |
| `customer.subscription.deleted` | Cancellation | Revoke access |
| `invoice.payment_failed` | Payment failed | Notify user, retry |
| `invoice.paid` | Invoice paid | Confirm payment |

### Verify webhook signature

```javascript
const event = stripe.webhooks.constructEvent(
  payload,
  sig,
  webhookSecret
);
```

## CLI Commands

```bash
# Listen to webhooks locally
stripe listen --forward-to localhost:3000/webhooks

# Trigger 测试 events
stripe trigger checkout.session.completed

# List recent events
stripe events list --limit 10

# Get resource
stripe customers retrieve cus_xxx
```

## Key Objects

- **客户** - User billing profile
- **Subscription** - Recurring billing
- **Price** - Pricing configuration
- **产品** - What you sell
- **Invoice** - Billing document
- **PaymentIntent** - One-time payment
- **Checkout Session** - Hosted payment page

## 适用场景

- Processing payments
- Managing subscriptions
- Creating checkout flows
- Handling billing portal
- Querying 客户 data
- Revenue 分析

## 速率限制

- 100 read requests per second
- 100 write requests per second
- Higher limits available on request

## 相关技能

- pricing-strategy
- referral-program (Stripe-integrated affiliate tools)
- 分析-跟踪 (revenue 跟踪)
