# Wistia

视频 hosting, management, and 分析 平台 built for marketers with detailed engagement 跟踪.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Data API (v1/modern), Stats API, Upload API |
| MCP | - | 不可用 |
| CLI | ✓ | [wistia.js](../clis/wistia.js) |
| SDK | ✓ | Ruby (official), community wrappers for other languages |

## 认证方式

- **类型**: Bearer Token
- **请求头**: `Authorization: Bearer {api_token}`
- **Get key**: 账户 Settings > API tab at https://账户.wistia.com/账户/API
- **Note**: Only 账户 Owners can create/manage tokens. Tokens can only be copied when first created.

## 常见代理操作

### List all projects

```bash
GET https://api.wistia.com/v1/projects.json?page=1&per_page=25
```

### Create a project

```bash
POST https://api.wistia.com/v1/projects.json

{
  "name": "Marketing Videos Q1"
}
```

### List all media

```bash
GET https://api.wistia.com/v1/medias.json?page=1&per_page=25
```

### Get media details

```bash
GET https://api.wistia.com/v1/medias/{media_hashed_id}.json
```

### Get media stats

```bash
GET https://api.wistia.com/v1/medias/{media_hashed_id}/stats.json
```

### Get 账户-wide stats

```bash
GET https://api.wistia.com/v1/stats/account.json
```

### Get media engagement data (heatmap)

```bash
GET https://api.wistia.com/v1/stats/medias/{media_id}/engagement.json
```

### Get media stats by date

```bash
GET https://api.wistia.com/v1/stats/medias/{media_id}/by_date.json?start_date=2026-01-01&end_date=2026-01-31
```

### List visitors

```bash
GET https://api.wistia.com/v1/stats/visitors.json?page=1&per_page=25
```

### List viewing events

```bash
GET https://api.wistia.com/v1/stats/events.json?media_id={media_id}
```

### Update media metadata

```bash
PUT https://api.wistia.com/v1/medias/{media_hashed_id}.json

{
  "name": "Updated Video Title",
  "description": "New description"
}
```

### List captions for a 视频

```bash
GET https://api.wistia.com/v1/medias/{media_hashed_id}/captions.json
```

## API Versions

Wistia has two API versions:
- **v1** (`/v1/`) - Legacy, perpetually supported, no breaking changes
- **modern** (`/modern/`) - Current version, date-based versioning via `X-Wistia-Api-Version` 请求头

The CLI uses v1 for maximum stability.

## 核心指标

### Media Stats
- `plays` - Total 视频 plays
- `visitors` - Unique visitors
- `pageLoads` - Page load count
- `averagePercentWatched` - Average watch percentage
- `percentOfVisitorsClickingPlay` - Play click rate

### Engagement Data
- Heatmap data showing exactly where viewers watch, rewatch, and drop off
- Per-second engagement breakdown

### 账户 Stats
- `total_medias` - Total 视频 count
- `total_plays` - 账户-wide plays
- `total_hours_watched` - Total hours of 视频 watched

## Parameters

### Media List Parameters
- `page` - Page number (default: 1)
- `per_page` - Results per page (default: 25, max: 100)
- `project_id` - Filter by project
- `name` - Filter by name
- `type` - Filter by 类型 (视频, Audio, Image, etc.)

### Stats Date Parameters
- `start_date` - Start date (YYYY-MM-DD)
- `end_date` - End date (YYYY-MM-DD)

## 适用场景

- Hosting 营销 and 产品 videos with 分析
- 跟踪 视频 engagement and viewer behavior
- A/B 测试 视频 thumbnails and CTAs
- Embedding videos with custom player branding
- Analyzing which parts of videos drive engagement
- Lead generation via 视频 email gates

## 速率限制

- 600 requests per minute per 账户
- Exceeding returns HTTP 429 with `Retry-After` 请求头
- Asset access (media file downloads) does not count toward limit
- Events data returns records from past 2 years only

## 相关技能

- 视频-营销
- content-repurposing
- landing-page-optimization
- lead-generation
