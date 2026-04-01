# Tolt

Affiliate program management for SaaS, with Stripe and Paddle integration.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for affiliates, referrals, payouts |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | - | JavaScript snippet for 跟踪 |

## 认证方式

- **类型**: API Key
- **请求头**: `Authorization: Bearer {api_key}`
- **Get key**: Settings > API in Tolt dashboard

## 常见代理操作

### List affiliates

```bash
GET https://api.tolt.io/v1/affiliates
```

### Get affiliate

```bash
GET https://api.tolt.io/v1/affiliates/{affiliate_id}
```

### Create affiliate

```bash
POST https://api.tolt.io/v1/affiliates

{
  "email": "affiliate@example.com",
  "name": "John Doe"
}
```

### List referrals

```bash
GET https://api.tolt.io/v1/referrals?affiliate_id={affiliate_id}
```

### Get referral by 客户

```bash
GET https://api.tolt.io/v1/referrals?customer_id={stripe_customer_id}
```

### List commissions

```bash
GET https://api.tolt.io/v1/commissions?affiliate_id={affiliate_id}
```

### Get payout history

```bash
GET https://api.tolt.io/v1/payouts?affiliate_id={affiliate_id}
```

### Update affiliate

```bash
PATCH https://api.tolt.io/v1/affiliates/{affiliate_id}

{
  "commission_rate": 30,
  "payout_method": "paypal",
  "paypal_email": "affiliate@paypal.com"
}
```

## JavaScript 跟踪

### Install snippet

```html
<script src="https://cdn.tolt.io/tolt.js" data-tolt="YOUR_PUBLIC_KEY"></script>
```

### Track signup

```javascript
window.tolt.signup(stripeCustomerId);
```

### Identify existing 客户

```javascript
window.tolt.identify(stripeCustomerId);
```

## Webhook Events

| 事件 | When |
|-------|------|
| `affiliate.created` | New affiliate registered |
| `affiliate.approved` | Affiliate approved |
| `referral.created` | New referral tracked |
| `referral.converted` | Referral converted to 客户 |
| `commission.created` | Commission earned |
| `payout.completed` | Payout sent |

## 核心特性

- **Stripe native** - Automatic commission 跟踪
- **Paddle support** - Works with Paddle billing
- **Affiliate dashboard** - White-labeled portal
- **Payout automation** - PayPal and Wise payouts
- **Custom commission tiers** - Different rates per affiliate

## Key Objects

- **Affiliate** - Partner in your program
- **Referral** - Tracked conversion
- **Commission** - Earned affiliate payment
- **Payout** - Processed payment to affiliate
- **Program** - 广告活动 configuration

## 适用场景

- Setting up SaaS affiliate programs
- Managing affiliate relationships
- 跟踪 Stripe or Paddle-based referrals
- Processing affiliate payouts
- Building affiliate dashboards

## 速率限制

- 100 requests per minute
- Higher limits on enterprise plans

## 相关技能

- referral-program
- pricing-strategy
