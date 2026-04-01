# Crossbeam

Partner ecosystem 平台 (now part of Reveal) for sharing 账户 data with partners to identify co-sell opportunities, overlapping 客户, and partner-sourced pipeline.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Partners, Populations, Overlaps, Reports, Threads |
| MCP | ✓ | [Claude connector](https://claude.com/connectors/crossbeam) |
| CLI | ✓ | [crossbeam.js](../clis/crossbeam.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: API Key
- **请求头**: `Authorization: Bearer {api_key}`
- **Get key**: Settings > API at https://app.crossbeam.com

## 常见代理操作

### List Partners

```bash
GET https://api.crossbeam.com/v1/partners
Authorization: Bearer {api_key}
```

### Get Partner Details

```bash
GET https://api.crossbeam.com/v1/partners/{id}
Authorization: Bearer {api_key}
```

### List Populations

```bash
GET https://api.crossbeam.com/v1/populations
Authorization: Bearer {api_key}
```

### List Overlaps

```bash
GET https://api.crossbeam.com/v1/overlaps?partner_id={partner_id}&population_id={population_id}
Authorization: Bearer {api_key}
```

### Get Overlap Details

```bash
GET https://api.crossbeam.com/v1/overlaps/{id}
Authorization: Bearer {api_key}
```

### 搜索 Accounts

```bash
GET https://api.crossbeam.com/v1/accounts/search?domain={domain}
Authorization: Bearer {api_key}
```

### List Reports

```bash
GET https://api.crossbeam.com/v1/reports
Authorization: Bearer {api_key}
```

### List Collaboration Threads

```bash
GET https://api.crossbeam.com/v1/threads
Authorization: Bearer {api_key}
```

## 核心指标

### Partner Data
- `id` - Partner ID
- `name` - Partner company name
- `status` - Partnership status (active, pending, etc.)
- `created_at` - When the partnership was established
- `populations_shared` - Number of shared populations

### Population Data
- `id` - Population ID
- `name` - Population name (e.g., "客户", "Open Opportunities")
- `record_count` - Number of records in population
- `partner_visibility` - What partners can see

### Overlap Data
- `id` - Overlap ID
- `partner_id` - Partner involved
- `population_id` - Population matched
- `account_name` - Overlapping 账户 name
- `overlap_type` - 类型 of overlap (客户, prospect, etc.)
- `match_confidence` - Match confidence score

### Report Data
- `id` - Report ID
- `name` - Report name
- `type` - Report 类型
- `created_at` - Creation date
- `results` - Report results data

## Parameters

### Overlaps List
- `partner_id` - Filter by specific partner
- `population_id` - Filter by specific population

### Accounts 搜索
- `domain` - Company domain to 搜索 for

## 适用场景

- Identifying co-sell opportunities with channel partners
- Finding overlapping 客户 and prospects across partner ecosystems
- Building partner-sourced pipeline by matching accounts
- 跟踪 partner influence on deals
- Creating 账户 mapping reports for partner meetings
- Prioritizing which partners to engage based on overlap data

## 速率限制

- 速率限制 vary by plan
- Standard: 100 requests/minute
- Pagination supported on list endpoints

## 相关技能

- revops
- sales-enablement
- referral-program
- competitor-alternatives
