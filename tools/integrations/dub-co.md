# Dub.co

Link management and attribution 平台 for modern 营销 teams.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for links, 分析, domains |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | TypeScript SDK available |

## 认证方式

- **类型**: API Key
- **请求头**: `Authorization: Bearer {api_key}`
- **Get key**: Settings > API Keys in Dub dashboard

## 常见代理操作

### Create short link

```bash
POST https://api.dub.co/links

{
  "url": "https://example.com/landing-page",
  "domain": "link.example.com",
  "key": "summer-sale",
  "tags": ["campaign:summer", "channel:email"]
}
```

### Get link by key

```bash
GET https://api.dub.co/links?domain=link.example.com&key=summer-sale
```

### List links

```bash
GET https://api.dub.co/links?domain=link.example.com&page=1
```

### Get link 分析

```bash
GET https://api.dub.co/analytics?domain=link.example.com&key=summer-sale&interval=30d
```

### Get 点击 by location

```bash
GET https://api.dub.co/analytics/country?domain=link.example.com&key=summer-sale
```

### Get 点击 by device

```bash
GET https://api.dub.co/analytics/device?domain=link.example.com&key=summer-sale
```

### Update link

```bash
PATCH https://api.dub.co/links/{link_id}

{
  "url": "https://example.com/new-landing-page",
  "tags": ["campaign:summer", "channel:social"]
}
```

### Delete link

```bash
DELETE https://api.dub.co/links/{link_id}
```

### Bulk create links

```bash
POST https://api.dub.co/links/bulk

[
  {"url": "https://example.com/page1", "key": "page1"},
  {"url": "https://example.com/page2", "key": "page2"}
]
```

## TypeScript SDK

### Install

```bash
npm install dub
```

### Usage

```typescript
import { Dub } from "dub";

const dub = new Dub({ token: "YOUR_API_KEY" });

// Create link
const link = await dub.links.create({
  url: "https://example.com",
  domain: "link.example.com"
});

// Get analytics
const analytics = await dub.analytics.retrieve({
  domain: "link.example.com",
  key: "summer-sale"
});
```

## 核心特性

- **Custom domains** - Use your own branded domains
- **Link 分析** - 点击, locations, devices, referrers
- **Tags** - Organize links by 广告活动, channel, etc.
- **QR codes** - Auto-generated for each link
- **Password protection** - Secure sensitive links
- **Expiration** - Time-limited links
- **Geo-targeting** - Redirect based on location

## 分析 Dimensions

- `clicks` - Total click count
- `country` - 点击 by country
- `city` - 点击 by city
- `device` - 点击 by device 类型
- `browser` - 点击 by browser
- `os` - 点击 by operating system
- `referer` - 点击 by referrer

## 适用场景

- Creating trackable 营销 links
- Building referral link systems
- 跟踪 广告活动 attribution
- A/B 测试 落地页s via links
- Generating branded short URLs
- Analyzing link 表现

## 速率限制

- Free: 1,000 links, 5 API requests/second
- Pro: Unlimited links, 50 API requests/second
- Enterprise: Custom limits

## 相关技能

- referral-program
- 分析-跟踪
- paid-ads
