# Mention Me

Enterprise referral 营销 平台 for 客户 advocacy.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for referrals, 客户, rewards |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | - | JavaScript widget for embedding |

## 认证方式

- **类型**: API Key
- **请求头**: `Authorization: Bearer {api_key}`
- **Environment**: Separate keys for sandbox and production

## 常见代理操作

### Create referral offer

```bash
POST https://api.mention-me.com/api/v2/referrer-offer

{
  "email": "customer@example.com",
  "firstname": "John",
  "lastname": "Doe",
  "order_number": "ORD-123",
  "order_total": 99.99,
  "order_currency": "USD"
}
```

### Get referral link for 客户

```bash
GET https://api.mention-me.com/api/v2/referrer/{customer_id}/share-links
```

### Record referee (referred 客户)

```bash
POST https://api.mention-me.com/api/v2/referee

{
  "email": "referred@example.com",
  "firstname": "Jane",
  "referrer_code": "JOHN123",
  "order_number": "ORD-456",
  "order_total": 149.99
}
```

### Get referral status

```bash
GET https://api.mention-me.com/api/v2/referral/{referral_id}
```

### List referrals for 客户

```bash
GET https://api.mention-me.com/api/v2/referrer/{customer_id}/referrals
```

### Get reward balance

```bash
GET https://api.mention-me.com/api/v2/referrer/{customer_id}/rewards
```

### Redeem reward

```bash
POST https://api.mention-me.com/api/v2/referrer/{customer_id}/rewards/redeem

{
  "reward_id": "RWD-123",
  "order_number": "ORD-789"
}
```

## JavaScript Widget

### Embed referral widget

```html
<div id="mmWrapper"></div>
<script>
  window.MentionMe = window.MentionMe || [];
  MentionMe.push({
    type: 'offer',
    customer: {
      email: 'customer@example.com',
      firstname: 'John',
      order_number: 'ORD-123'
    }
  });
</script>
<script src="https://tag.mention-me.com/client/{partner_code}.js" async></script>
```

### Name share widget

```javascript
MentionMe.push({
  type: 'nameShare',
  customer: {
    email: 'customer@example.com'
  }
});
```

## Webhook Events

| 事件 | When |
|-------|------|
| `referral.created` | New referral tracked |
| `referral.converted` | Referral completed purchase |
| `reward.earned` | Reward unlocked |
| `reward.redeemed` | Reward used |

## 核心特性

- **A/B 测试** - Built-in experiment framework
- **Fraud prevention** - Automatic fraud detection
- **Multi-channel** - Share via link, email, social
- **Name sharing** - Refer by name, not code
- **Segmentation** - Different offers by segment
- **分析** - Referral program reporting

## Key Objects

- **Referrer** - 客户 who refers
- **Referee** - 客户 who is referred
- **Referral** - Connection between referrer and referee
- **Offer** - Referral program configuration
- **Reward** - Incentive earned

## 适用场景

- Enterprise referral programs
- Multi-market referral 广告活动
- A/B 测试 referral offers
- Fraud-resistant referral 跟踪
- Name-based sharing programs

## 速率限制

- 1000 requests per minute
- Contact for higher limits

## 相关技能

- referral-program
- pricing-strategy
- 分析-跟踪
