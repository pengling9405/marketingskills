# Rewardful

Affiliate and referral 跟踪 for Stripe-based SaaS businesses.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for affiliates, referrals, commissions |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | - | API-only, JavaScript snippet for 跟踪 |

## 认证方式

- **类型**: API Key
- **请求头**: `Authorization: Bearer {api_secret}`
- **Get key**: Settings > API in Rewardful dashboard

## 常见代理操作

### List affiliates

```bash
GET https://api.getrewardful.com/v1/affiliates
```

### Get affiliate by ID

```bash
GET https://api.getrewardful.com/v1/affiliates/{affiliate_id}
```

### 搜索 affiliate by email

```bash
GET https://api.getrewardful.com/v1/affiliates?email=affiliate@example.com
```

### Get referral by Stripe 客户

```bash
GET https://api.getrewardful.com/v1/referrals?stripe_customer_id={customer_id}
```

### List referrals for affiliate

```bash
GET https://api.getrewardful.com/v1/referrals?affiliate_id={affiliate_id}
```

### Get commission details

```bash
GET https://api.getrewardful.com/v1/commissions/{commission_id}
```

### List commissions

```bash
GET https://api.getrewardful.com/v1/commissions?affiliate_id={affiliate_id}
```

### Create affiliate link

```bash
POST https://api.getrewardful.com/v1/affiliates/{affiliate_id}/links

{
  "token": "custom-link-token",
  "url": "https://example.com/pricing"
}
```

### Update affiliate

```bash
PUT https://api.getrewardful.com/v1/affiliates/{affiliate_id}

{
  "first_name": "John",
  "last_name": "Doe",
  "paypal_email": "john@example.com"
}
```

## JavaScript 跟踪

### Install snippet

```html
<script>
(function(w,r){w._rwq=r;w[r]=w[r]||function(){(w[r].q=w[r].q||[]).push(arguments)}})(window,'rewardful');
</script>
<script async src='https://r.wdfl.co/rw.js' data-rewardful='YOUR_API_KEY'></script>
```

### Track conversion manually

```javascript
rewardful('convert', { email: 'customer@example.com' });
```

## Webhook Events

| 事件 | When |
|-------|------|
| `affiliate.created` | New affiliate signs up |
| `affiliate.approved` | Affiliate approved |
| `referral.created` | New referral tracked |
| `referral.converted` | Referral becomes 客户 |
| `commission.created` | Commission generated |
| `commission.paid` | Commission paid out |

## Key Objects

- **Affiliate** - Partner promoting your 产品
- **Referral** - Tracked visit/lead from affiliate
- **Commission** - Earned payment for affiliate
- **广告活动** - Program with specific terms
- **Link** - 跟踪 URL for affiliate

## Integration with Stripe

Rewardful automatically:
1. Tracks referral cookie when user visits via affiliate link
2. Associates Stripe 客户 with referral on checkout
3. Creates commissions when subscriptions are paid
4. Handles recurring commissions for subscriptions

## 适用场景

- Setting up affiliate/referral programs for SaaS
- 跟踪 referral attribution from Stripe payments
- Managing affiliate relationships
- Processing affiliate payouts
- Analyzing referral program 表现

## 速率限制

- 120 requests per minute
- Contact support for higher limits

## 相关技能

- referral-program
- pricing-strategy
