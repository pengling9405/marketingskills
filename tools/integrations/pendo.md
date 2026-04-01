# Pendo

产品 分析 and in-app 指导 平台 for 跟踪 user behavior, measuring feature adoption, and delivering targeted in-app messages.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | 特性, Pages, Guides, Visitors, Accounts, Reports, Metadata |
| MCP | - | 不可用 |
| CLI | ✓ | [pendo.js](../clis/pendo.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: Integration Key
- **请求头**: `x-pendo-integration-key: {key}`
- **Get key**: Settings > Integrations at https://app.pendo.io

## 常见代理操作

### List 特性

```bash
GET https://app.pendo.io/api/v1/feature
```

### Get Feature Details

```bash
GET https://app.pendo.io/api/v1/feature/{featureId}
```

### List Pages

```bash
GET https://app.pendo.io/api/v1/page
```

### Get Page Details

```bash
GET https://app.pendo.io/api/v1/page/{pageId}
```

### List Guides

```bash
GET https://app.pendo.io/api/v1/guide?state=public
```

### Get Guide Details

```bash
GET https://app.pendo.io/api/v1/guide/{guideId}
```

### Get Visitor Data

```bash
GET https://app.pendo.io/api/v1/visitor/{visitorId}
```

### 搜索 Visitors

```bash
POST https://app.pendo.io/api/v1/aggregation

{
  "response": { "mimeType": "application/json" },
  "request": {
    "pipeline": [
      { "source": { "visitors": null } },
      { "filter": "lastVisitedAt > 1700000000000" }
    ]
  }
}
```

### Get 账户 Data

```bash
GET https://app.pendo.io/api/v1/account/{accountId}
```

### 搜索 Accounts

```bash
POST https://app.pendo.io/api/v1/aggregation

{
  "response": { "mimeType": "application/json" },
  "request": {
    "pipeline": [
      { "source": { "accounts": null } },
      { "filter": "metadata.auto.lastupdated > 1700000000000" }
    ]
  }
}
```

### Run Funnel Report

```bash
POST https://app.pendo.io/api/v1/aggregation

{
  "response": { "mimeType": "application/json" },
  "request": {
    "pipeline": [
      { "source": { "visitors": null, "timeSeries": { "period": "dayRange", "first": 1700000000000, "last": 1700600000000 } } },
      { "identified": "visitorId" },
      { "filter": "pageId == \"page-id-1\"" },
      { "filter": "pageId == \"page-id-2\"" }
    ]
  }
}
```

### List Metadata Fields

```bash
GET https://app.pendo.io/api/v1/metadata/schema/visitor
GET https://app.pendo.io/api/v1/metadata/schema/account
GET https://app.pendo.io/api/v1/metadata/schema/parentAccount
```

## 核心指标

### Feature Data
- `id` - Feature ID
- `name` - Feature name
- `kind` - Feature 类型
- `elementPath` - CSS selector for the tracked element
- `pageId` - Associated page ID
- `numEvents` - 事件 count
- `numVisitors` - Unique visitor count

### Page Data
- `id` - Page ID
- `name` - Page name
- `rules` - URL matching rules
- `numEvents` - Pageview count
- `numVisitors` - Unique visitor count

### Guide Data
- `id` - Guide ID
- `name` - Guide name
- `state` - Guide state (draft, staged, public, disabled)
- `launchMethod` - How the guide is triggered
- `steps` - Guide step definitions
- `numSteps` - Number of 步骤
- `numViews` - Total views
- `numVisitors` - Unique visitors who saw the guide

### Visitor Data
- `visitorId` - Unique visitor identifier
- `lastVisitedAt` - Last visit timestamp
- `firstVisit` - First visit timestamp
- `numEvents` - Total 事件 count
- `metadata` - Custom visitor metadata

### 账户 Data
- `accountId` - Unique 账户 identifier
- `lastVisitedAt` - Last visit from any 账户 member
- `numVisitors` - Number of visitors in the 账户
- `metadata` - Custom 账户 metadata

## Parameters

### Guide Filtering
- `state` - Filter by state: draft, staged, public, disabled

### Aggregation Queries
- `source` - Data 来源: visitors, accounts, 特性, pages, guides
- `filter` - Expression-based filtering
- `sort` - Sort results
- `limit` - Max results to return
- `timeSeries` - Time range with period, first, last

### Metadata Kinds
- `visitor` - Visitor metadata schema
- `account` - 账户 metadata schema
- `parentAccount` - Parent 账户 metadata schema

## 适用场景

- 跟踪 feature adoption and usage patterns
- Building and managing in-app onboarding guides
- Analyzing user behavior across pages and 特性
- Segmenting users by engagement level
- Running funnel analysis on user journeys
- Identifying at-risk accounts based on usage decline
- A/B 测试 in-app messages and tooltips

## 速率限制

- 速率限制 vary by plan
- Standard: 500 requests per minute
- Aggregation queries: may take longer for large datasets
- Use pagination for large result sets

## 相关技能

- 分析-跟踪
- onboarding-cro
- churn-prevention
- ab-test-配置方式
