# Coupler.io

Data integration 平台 that connects 营销, sales, 分析, and e-commerce data sources to destinations like spreadsheets, BI tools, and data warehouses with automated scheduling.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Importers, Runs, Sources, Destinations |
| MCP | ✓ | [Claude connector](https://claude.com/connectors/coupler-io) |
| CLI | ✓ | [coupler.js](../clis/coupler.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: API Key
- **请求头**: `Authorization: Bearer {api_key}`
- **Get key**: Settings > API at https://app.coupler.io

## 常见代理操作

### List Importers

```bash
GET https://api.coupler.io/v1/importers
```

### Get Importer Details

```bash
GET https://api.coupler.io/v1/importers/{id}
```

### Trigger an Importer Run

```bash
POST https://api.coupler.io/v1/importers/{id}/run
```

### Create an Importer

```bash
POST https://api.coupler.io/v1/importers

{
  "source_type": "google_analytics",
  "destination_type": "google_sheets",
  "name": "GA4 to Sheets Daily"
}
```

### Delete an Importer

```bash
DELETE https://api.coupler.io/v1/importers/{id}
```

### List Runs for an Importer

```bash
GET https://api.coupler.io/v1/importers/{id}/runs
```

### Get Run Details

```bash
GET https://api.coupler.io/v1/runs/{id}
```

### List 可用 Sources

```bash
GET https://api.coupler.io/v1/sources
```

### List 可用 Destinations

```bash
GET https://api.coupler.io/v1/destinations
```

## 核心指标

### Importer Data
- `id` - Importer ID
- `name` - Importer name
- `source_type` - 来源 connector 类型
- `destination_type` - 目标 connector 类型
- `schedule` - Automation schedule
- `status` - Current status
- `last_run_at` - Last run timestamp

### Run Data
- `id` - Run ID
- `importer_id` - Parent importer
- `status` - Run status (pending, running, completed, failed)
- `started_at` - Start timestamp
- `finished_at` - Finish timestamp
- `rows_imported` - Number of rows processed
- `error` - Error message if failed

## Parameters

### Importer Creation
- `source_type` - 来源 connector (e.g., google_analytics, google_ads, facebook_ads, hubspot, shopify, stripe, airtable)
- `destination_type` - 目标 connector (e.g., google_sheets, bigquery, snowflake, postgresql)
- `name` - Importer name
- `schedule` - Automation schedule (e.g., hourly, daily, weekly)

### Supported Sources
- **分析**: Google 分析, Adobe 分析
- **Ads**: Google Ads, Facebook Ads, LinkedIn Ads, TikTok Ads
- **CRM**: HubSpot, Salesforce, Pipedrive
- **E-commerce**: Shopify, Stripe, WooCommerce
- **Other**: Airtable, Google Sheets, BigQuery, MySQL, PostgreSQL

### Supported Destinations
- **Spreadsheets**: Google Sheets, Excel Online
- **BI Tools**: Looker Studio, Power BI, Tableau
- **Data Warehouses**: BigQuery, Snowflake, Redshift
- **Databases**: PostgreSQL, MySQL

## 适用场景

- Automating 营销 data pipelines from ads and 分析 platforms
- Consolidating multi-channel 广告活动 data into a single 目标
- Scheduling recurring data syncs from CRM to spreadsheets or BI tools
- Building 营销 dashboards with fresh data from multiple sources
- Exporting e-commerce data for reporting and 分析
- Connecting data sources without writing custom ETL code

## 速率限制

- 速率限制 vary by plan
- Standard: API access available on Professional and higher plans
- Importer run frequency depends on plan tier

## 相关技能

- 分析-跟踪
- paid-ads
- revops
