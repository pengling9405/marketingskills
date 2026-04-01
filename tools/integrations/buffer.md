# Buffer

Social media scheduling, publishing, and 分析 平台 for managing multiple social profiles.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API v1 for profiles, updates, scheduling |
| MCP | - | 不可用 |
| CLI | ✓ | [buffer.js](../clis/buffer.js) |
| SDK | - | No official SDK; legacy API still supported |

## 认证方式

- **类型**: OAuth 2.0 Bearer Token
- **请求头**: `Authorization: Bearer {access_token}`
- **Get key**: Register app at https://buffer.com/developers/apps then complete OAuth flow
- **Note**: Buffer is no longer accepting new developer app registrations; existing apps continue to work. New public API is in development at https://buffer.com/developer-API

## 常见代理操作

### Get user info

```bash
GET https://api.bufferapp.com/1/user.json

Authorization: Bearer {token}
```

### List connected profiles

```bash
GET https://api.bufferapp.com/1/profiles.json

Authorization: Bearer {token}
```

### Get profile posting schedules

```bash
GET https://api.bufferapp.com/1/profiles/{profile_id}/schedules.json
```

### Create a scheduled post

```bash
POST https://api.bufferapp.com/1/updates/create.json
Content-Type: application/x-www-form-urlencoded

profile_ids[]={profile_id}&text=Your+post+content&scheduled_at=2026-03-01T10:00:00Z
```

### Get pending updates for a profile

```bash
GET https://api.bufferapp.com/1/profiles/{profile_id}/updates/pending.json?count=25
```

### Get sent updates for a profile

```bash
GET https://api.bufferapp.com/1/profiles/{profile_id}/updates/sent.json?count=25
```

### Publish a pending update immediately

```bash
POST https://api.bufferapp.com/1/updates/{update_id}/share.json
```

### Delete an update

```bash
POST https://api.bufferapp.com/1/updates/{update_id}/destroy.json
```

### Reorder queue

```bash
POST https://api.bufferapp.com/1/profiles/{profile_id}/updates/reorder.json
Content-Type: application/x-www-form-urlencoded

order[]={update_id_1}&order[]={update_id_2}&order[]={update_id_3}
```

## API Pattern

Buffer API v1 uses `.json` extensions on all endpoints. POST requests use `application/x-www-form-urlencoded` content 类型. Array parameters use bracket notation (e.g., `profile_ids[]`).

Responses include a `success` boolean for mutation 操作.

## 核心指标

### Profile 指标
- `followers` - Follower count for connected profile
- `service` - 平台 name (twitter, facebook, instagram, linkedin, etc.)

### Update 指标 (sent updates)
- `statistics.reach` - Post reach
- `statistics.clicks` - Link 点击
- `statistics.retweets` - Retweets/shares
- `statistics.favorites` - Likes/favorites
- `statistics.mentions` - Mentions

## Parameters

### Update Create Parameters
- `profile_ids[]` - Required. Array of profile IDs to post to
- `text` - Required. Post content
- `scheduled_at` - ISO 8601 timestamp for scheduling
- `now` - Set to `true` to publish immediately
- `top` - Set to `true` to add to top of queue
- `shorten` - Set to `true` to auto-shorten links
- `media[photo]` - URL to photo attachment
- `media[thumbnail]` - URL to thumbnail
- `media[link]` - URL for link attachment

## 适用场景

- Scheduling social media posts across multiple platforms
- Managing social media content queues
- Analyzing post 表现 across channels
- Automating social media publishing 工作流
- Coordinating team social media activity

## 速率限制

- 60 authenticated requests per user per minute
- Exceeding returns HTTP 429
- Higher limits available by contacting hello@buffer.com

## 相关技能

- social-media-calendar
- content-repurposing
- social-proof
- launch-sequence
