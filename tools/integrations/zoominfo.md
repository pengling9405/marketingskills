# ZoomInfo

B2B contact database and intent data 平台 with 100M+ business contacts and company intelligence for sales and 营销 teams.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Contact 搜索, Company 搜索, Enrichment, Intent Data, Scoops |
| MCP | ✓ | [Claude connector](https://claude.com/connectors/zoominfo) |
| CLI | ✓ | [zoominfo.js](../clis/zoominfo.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: JWT Token (Bearer)
- **Flow**: POST `/authenticate` with username + password, receive JWT token
- **请求头**: `Authorization: Bearer {jwt_token}`
- **Env vars**: `ZOOMINFO_USERNAME` + `ZOOMINFO_PRIVATE_KEY` or `ZOOMINFO_ACCESS_TOKEN`
- **Get credentials**: Contact ZoomInfo sales or admin portal at https://app.zoominfo.com

## 常见代理操作

### Authenticate

```bash
POST https://api.zoominfo.com/authenticate

{
  "username": "user@company.com",
  "password": "private-key-here"
}
```

### Contact 搜索

```bash
POST https://api.zoominfo.com/search/contact

{
  "jobTitle": ["VP Marketing"],
  "companyName": ["Acme Corp"],
  "managementLevel": ["VP"],
  "rpp": 25,
  "page": 1
}
```

### Contact Enrichment

```bash
POST https://api.zoominfo.com/enrich/contact

{
  "matchEmail": ["jane@acme.com"]
}
```

### Company 搜索

```bash
POST https://api.zoominfo.com/search/company

{
  "companyName": ["Acme"],
  "industry": ["Software"],
  "employeeCountMin": 50,
  "revenueMin": 10000000,
  "rpp": 25,
  "page": 1
}
```

### Company Enrichment

```bash
POST https://api.zoominfo.com/enrich/company

{
  "matchCompanyWebsite": ["acme.com"]
}
```

### Intent Data Lookup

```bash
POST https://api.zoominfo.com/lookup/intent

{
  "topicId": ["marketing-automation"],
  "companyId": ["123456"]
}
```

### Scoops Lookup

```bash
POST https://api.zoominfo.com/lookup/scoops

{
  "companyId": ["123456"],
  "rpp": 25,
  "page": 1
}
```

## 核心指标

### Contact Data
- `firstName`, `lastName` - Name
- `jobTitle` - Job title
- `email` - Verified email
- `phone` - Direct phone
- `linkedinUrl` - LinkedIn profile
- `companyName` - Company name
- `managementLevel` - Seniority level
- `department` - Department

### Company Data
- `companyName` - Company name
- `website` - Website URL
- `employeeCount` - Employee count
- `industry` - Industry
- `revenue` - Annual revenue
- `techStack` - Technologies used
- `fundingAmount` - Total funding
- `companyCity`, `companyState`, `companyCountry` - Location

### Intent Data
- `topicName` - Intent topic
- `signalScore` - Signal strength
- `audienceStrength` - 受众 engagement level
- `firstSeenDate`, `lastSeenDate` - Signal timeframe

## Parameters

### Contact 搜索
- `jobTitle` - Array of job titles
- `companyName` - Array of company names
- `managementLevel` - Array: C-Level, VP, Director, Manager, Staff
- `department` - Array: 营销, Sales, Engineering, Finance, etc.
- `personLocationCity` - Array of cities
- `personLocationState` - Array of states
- `personLocationCountry` - Array of countries
- `rpp` - Results per page (default: 25, max: 100)
- `page` - Page number (default: 1)

### Contact Enrichment
- `matchEmail` - Array of email addresses
- `personId` - Array of ZoomInfo person IDs
- `matchFirstName` + `matchLastName` + `matchCompanyName` - Alternative lookup

### Company 搜索
- `companyName` - Array of company names
- `industry` - Array of industries
- `employeeCountMin` / `employeeCountMax` - Employee count range
- `revenueMin` / `revenueMax` - Revenue range
- `companyLocationCity` - Array of cities
- `rpp` - Results per page
- `page` - Page number

### Company Enrichment
- `matchCompanyWebsite` - Array of domains
- `companyId` - Array of ZoomInfo company IDs

### Intent Data
- `topicId` - Array of intent topic IDs
- `companyId` - Array of company IDs

## 适用场景

- Identifying in-market accounts with intent signals
- Building targeted contact lists by role, seniority, and company
- Enriching leads with verified contact data and firmographics
- Finding decision-makers at target accounts for ABM
- 跟踪 company news and leadership changes via scoops
- Prioritizing outreach based on buyer intent signals

## 速率限制

- 速率限制 vary by plan and endpoint
- Standard: ~200 requests/minute
- Bulk endpoints: batched requests recommended
- 认证 tokens expire after ~12 hours

## 相关技能

- cold-email
- revops
- sales-enablement
- competitor-alternatives
