# Clay

Data enrichment and outbound automation 平台 for building lead lists with waterfall enrichment across 75+ data providers.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Tables, People Enrichment, Company Enrichment |
| MCP | ✓ | [Claude connector](https://claude.com/connectors/clay) |
| CLI | ✓ | [clay.js](../clis/clay.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: API Key (Bearer token)
- **请求头**: `Authorization: Bearer {api_key}`
- **Get key**: Settings > API at https://app.clay.com

## 常见代理操作

### List Tables

```bash
GET https://api.clay.com/v3/tables

Authorization: Bearer {api_key}
```

### Get Table Details

```bash
GET https://api.clay.com/v3/tables/{table_id}

Authorization: Bearer {api_key}
```

### Get Table Rows

```bash
GET https://api.clay.com/v3/tables/{table_id}/rows?page=1&per_page=25

Authorization: Bearer {api_key}
```

### Add Row to Table

```bash
POST https://api.clay.com/v3/tables/{table_id}/rows

{
  "first_name": "Jane",
  "last_name": "Doe",
  "company": "Acme Inc",
  "email": "jane@acme.com"
}
```

### People Enrichment

```bash
POST https://api.clay.com/v3/people/enrich

{
  "email": "jane@acme.com"
}
```

### Company Enrichment

```bash
POST https://api.clay.com/v3/companies/enrich

{
  "domain": "acme.com"
}
```

## 核心指标

### Person Data
- `first_name`, `last_name` - Name
- `email` - Email address
- `title` - Job title
- `linkedin_url` - LinkedIn profile
- `company` - Company name
- `location` - Location
- `seniority` - Seniority level

### Company Data
- `name` - Company name
- `domain` - Website domain
- `industry` - Industry
- `employee_count` - Number of employees
- `revenue` - Estimated revenue
- `location` - Headquarters location
- `technologies` - Tech stack
- `description` - Company description

### Table Data
- `id` - Table ID
- `name` - Table name
- `row_count` - Number of rows
- `columns` - Column definitions
- `created_at` - Creation timestamp
- `updated_at` - Last update timestamp

## Parameters

### Tables
- `page` - Page number (default: 1)
- `per_page` - Results per page (default: 25)

### People Enrichment
- `email` - Email address
- `linkedin_url` - LinkedIn profile URL
- `first_name` + `last_name` - Name-based lookup

### Company Enrichment
- `domain` - Company domain (e.g., "acme.com")

### Add Row
- Fields are dynamic and match the table's column definitions
- Pass data as key-value pairs matching column names

## 适用场景

- Building enriched prospect lists with waterfall enrichment across multiple providers
- Enriching leads with person and company data from 75+ sources
- Automating outbound 工作流 with enriched data
- Finding verified contact info (emails, phone numbers, social profiles)
- Company research and firmographic 分析
- Triggering enrichment 工作流 via webhooks
- Syncing enriched data back to CRM or outbound tools

## 速率限制

- 速率限制 vary by plan
- Standard: 100 requests/minute
- Enterprise plans have higher limits
- Enrichment credits consumed per lookup vary by data provider
- Webhook endpoints accept data continuously

## 相关技能

- cold-email
- revops
- sales-enablement
- competitor-alternatives
