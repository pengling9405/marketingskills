# Trustpilot

Business review management 平台 for collecting, managing, and showcasing 客户 reviews.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Business Units, Reviews, Invitations, Tags |
| MCP | - | 不可用 |
| CLI | ✓ | [trustpilot.js](../clis/trustpilot.js) |
| SDK | ✓ | Node.js (official), community wrappers |

## 认证方式

- **类型**: API Key (public endpoints) + OAuth 2.0 (private endpoints)
- **Public 请求头**: `apikey: {YOUR_API_KEY}`
- **Private 请求头**: `Authorization: Bearer {access_token}`
- **OAuth Grant**: Client Credentials (`Basic base64(API_KEY:API_SECRET)`)
- **Token Lifetime**: Access tokens expire after 100 hours, refresh tokens after 30 days
- **Get credentials**: https://businessapp.b2b.trustpilot.com/ > Integrations > API

## 常见代理操作

### 搜索 for a business unit

```bash
GET https://api.trustpilot.com/v1/business-units/search?query=example.com&limit=10

Headers:
  apikey: {API_KEY}
```

### Get business unit details

```bash
GET https://api.trustpilot.com/v1/business-units/{businessUnitId}

Headers:
  apikey: {API_KEY}
```

### Get business profile info

```bash
GET https://api.trustpilot.com/v1/business-units/{businessUnitId}/profileinfo

Headers:
  apikey: {API_KEY}
```

### List public reviews

```bash
GET https://api.trustpilot.com/v1/business-units/{businessUnitId}/reviews?perPage=20&orderBy=createdat.desc

Headers:
  apikey: {API_KEY}
```

### List private reviews (with 客户 data)

```bash
GET https://api.trustpilot.com/v1/private/business-units/{businessUnitId}/reviews?perPage=20

Headers:
  Authorization: Bearer {access_token}
```

### Reply to a review

```bash
POST https://api.trustpilot.com/v1/private/reviews/{reviewId}/reply

Headers:
  Authorization: Bearer {access_token}

{
  "message": "Thank you for your feedback!"
}
```

### Send email invitation

```bash
POST https://api.trustpilot.com/v1/private/business-units/{businessUnitId}/email-invitations

Headers:
  Authorization: Bearer {access_token}

{
  "consumerEmail": "customer@example.com",
  "consumerName": "Jane Doe",
  "referenceNumber": "order-123",
  "redirectUri": "https://example.com/thanks"
}
```

### Generate review invitation link

```bash
POST https://api.trustpilot.com/v1/private/business-units/{businessUnitId}/invitation-links

Headers:
  Authorization: Bearer {access_token}

{
  "email": "customer@example.com",
  "name": "Jane Doe",
  "referenceId": "order-123",
  "redirectUri": "https://example.com/thanks"
}
```

### List invitation templates

```bash
GET https://api.trustpilot.com/v1/private/business-units/{businessUnitId}/templates

Headers:
  Authorization: Bearer {access_token}
```

### Add tags to a review

```bash
PUT https://api.trustpilot.com/v1/private/reviews/{reviewId}/tags

Headers:
  Authorization: Bearer {access_token}

{
  "tags": [{ "group": "sentiment", "value": "positive" }]
}
```

## 核心指标

### Business Unit 指标
- `numberOfReviews` - Total review count
- `trustScore` - Overall trust score (1-5)
- `stars` - Star rating displayed
- `status` - Claim status (claimed, unclaimed)

### Review 指标
- `stars` - Individual review star rating (1-5)
- `language` - Review language code
- `createdAt` - Review creation timestamp
- `isVerified` - Whether the review is verified
- `status` - Review status (active, reported, flagged)

## Parameters

### Review Filters
- `stars` - Filter by star rating (1-5)
- `language` - Filter by language code (e.g., `en`)
- `orderBy` - Sort order (`createdat.desc`, `createdat.asc`, `stars.desc`, `stars.asc`)
- `perPage` - Results per page (max 100)

### Invitation Parameters
- `consumerEmail` - Recipient email (required)
- `consumerName` - Recipient name (required)
- `referenceNumber` - Order or transaction 参考
- `templateId` - Email template ID
- `redirectUri` - URL to redirect after review submission
- `senderEmail` - Custom sender email
- `replyTo` - Custom reply-to address

## 适用场景

- Collecting and managing 客户 reviews at scale
- Automating post-purchase review invitation flows
- Monitoring brand reputation and review sentiment
- Responding to 客户 feedback programmatically
- Showcasing TrustScore and reviews on 营销 pages
- Tagging and categorizing reviews for 分析

## 速率限制

- Recommended: no more than 833 calls per 5 minutes (10K/hour)
- Throttled at more than 1 request per second
- Rate limit 请求头 returned in responses
- Use webhooks instead of polling where possible

## 相关技能

- reputation-management
- 客户-feedback
- review-generation
- social-proof
- post-purchase-flow
