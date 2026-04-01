# Ahrefs

SEO 工具集 for backlink analysis, 关键词 research, and competitive research.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for Site Explorer, 关键词 Explorer |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | - | API-only |

## 认证方式

- **类型**: API Token
- **请求头**: `Authorization: Bearer {api_token}`
- **获取令牌**： 账户 Settings > API in Ahrefs dashboard

## 常见代理操作

### 域名评级

```bash
GET https://api.ahrefs.com/v3/site-explorer/domain-rating?target=example.com

Authorization: Bearer {api_token}
```

### 反向链接概览

```bash
GET https://api.ahrefs.com/v3/site-explorer/backlinks-stats?target=example.com&mode=domain

Authorization: Bearer {api_token}
```

### 引荐域名

```bash
GET https://api.ahrefs.com/v3/site-explorer/refdomains?target=example.com&mode=domain&limit=100

Authorization: Bearer {api_token}
```

### 反向链接列表

```bash
GET https://api.ahrefs.com/v3/site-explorer/backlinks?target=example.com&mode=domain&limit=100

Authorization: Bearer {api_token}
```

### 自然搜索关键词

```bash
GET https://api.ahrefs.com/v3/site-explorer/organic-keywords?target=example.com&mode=domain&country=us&limit=100

Authorization: Bearer {api_token}
```

### 顶级页面

```bash
GET https://api.ahrefs.com/v3/site-explorer/top-pages?target=example.com&mode=domain&country=us&limit=50

Authorization: Bearer {api_token}
```

### 关键词概览

```bash
GET https://api.ahrefs.com/v3/keywords-explorer/overview?keywords=keyword1,keyword2&country=us

Authorization: Bearer {api_token}
```

### 关键词建议

```bash
GET https://api.ahrefs.com/v3/keywords-explorer/matching-terms?keyword=seed+keyword&country=us&limit=100

Authorization: Bearer {api_token}
```

### SERP 概览

```bash
GET https://api.ahrefs.com/v3/keywords-explorer/serp-overview?keyword=target+keyword&country=us

Authorization: Bearer {api_token}
```

## 核心指标

### Domain 指标
- `domain_rating` - Domain Rating (DR)
- `ahrefs_rank` - Ahrefs Rank
- `referring_domains` - Referring domains count
- `backlinks` - Total backlinks
- `organic_traffic` - Estimated organic traffic

### 关键词 指标
- `volume` - Monthly 搜索 volume
- `keyword_difficulty` - KD score (0-100)
- `cpc` - 每次点击成本
- `clicks` - Estimated monthly 点击
- `global_volume` - Global 搜索 volume

### Backlink Fields
- `url_from` - 来源 URL
- `url_to` - Target URL
- `anchor` - Anchor text
- `domain_rating_source` - 来源 DR
- `first_seen` - First discovery date

## 模式

- `domain` - Entire domain
- `subdomains` - Domain + subdomains
- `prefix` - URL prefix
- `exact` - Exact URL

## 适用场景

- Backlink 分析
- Link building 调研
- 关键词 调研
- Competitive 分析
- Content gap 分析
- Site audits

## 速率限制

- Varies by plan
- 500-5000 rows per request

## 相关技能

- seo-audit
- content-strategy
- competitor-alternatives
