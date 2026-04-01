# Adobe 分析

Enterprise 分析 平台 for cross-channel 衡量 and attribution.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Reporting API 2.0, Data Insertion API |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | AppMeasurement.js, Mobile SDKs, Launch |

## 认证方式

- **类型**: OAuth 2.0 (Service 账户 JWT)
- **配置**: Create integration in Adobe Developer Console
- **请求头**: `Authorization: Bearer {access_token}`

## 常见代理操作

### Get 报告 suite info

```bash
GET https://analytics.adobe.io/api/{company_id}/reportsuites

Authorization: Bearer {access_token}
x-api-key: {client_id}
```

### Get dimensions

```bash
GET https://analytics.adobe.io/api/{company_id}/dimensions?rsid={report_suite_id}

Authorization: Bearer {access_token}
x-api-key: {client_id}
```

### Get 指标

```bash
GET https://analytics.adobe.io/api/{company_id}/metrics?rsid={report_suite_id}

Authorization: Bearer {access_token}
x-api-key: {client_id}
```

### Run 报告

```bash
POST https://analytics.adobe.io/api/{company_id}/reports

{
  "rsid": "{report_suite_id}",
  "globalFilters": [{
    "type": "dateRange",
    "dateRange": "2024-01-01T00:00:00/2024-01-31T23:59:59"
  }],
  "metricContainer": {
    "metrics": [
      {"id": "metrics/visits"},
      {"id": "metrics/pageviews"},
      {"id": "metrics/orders"}
    ]
  },
  "dimension": "variables/evar1"
}
```

### Get segments

```bash
GET https://analytics.adobe.io/api/{company_id}/segments?rsid={report_suite_id}

Authorization: Bearer {access_token}
x-api-key: {client_id}
```

### Data Insertion (server-side)

```bash
POST https://{tracking_server}/b/ss/{report_suite_id}/0

<?xml version="1.0" encoding="UTF-8"?>
<request>
  <visitorID>user_123</visitorID>
  <events>event1</events>
  <eVar1>campaign_name</eVar1>
  <prop1>page_type</prop1>
</request>
```

## AppMeasurement.js

```javascript
// Initialize
var s = s_gi('report_suite_id');
s.trackingServer = 'metrics.example.com';

// Set variables
s.pageName = 'Home Page';
s.channel = 'Marketing';
s.eVar1 = 'campaign_name';
s.events = 'event1';

// Track page view
s.t();

// Track link
s.tl(this, 'o', 'Button Click');
```

## 关键概念

- **Report Suite** - Data container
- **eVars** - Conversion variables (persistent)
- **props** - Traffic variables (hit-level)
- **Events** - Success 指标
- **Segments** - User/visit filters
- **Calculated 指标** - Derived 指标

## 常见 Dimensions

- `variables/page` - Page name
- `variables/evar1` - Custom conversion variable
- `variables/prop1` - Custom traffic variable
- `variables/marketingchannel` - 营销 channel
- `variables/referringdomain` - Referring domain

## 常见 指标

- `metrics/visits` - Visits
- `metrics/pageviews` - Page views
- `metrics/uniquevisitors` - Unique visitors
- `metrics/orders` - Orders
- `metrics/revenue` - Revenue

## 适用场景

- Enterprise-scale 分析
- Cross-channel attribution
- Integration with Adobe Experience Cloud
- Advanced segmentation
- Data warehouse exports

## 速率限制

- 12 requests/second per company
- 120 requests/minute

## 相关技能

- 分析-跟踪
- ab-test-setup
- paid-ads
