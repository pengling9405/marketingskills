# SEMrush

SEO and competitive analysis 平台 for 关键词 research and site audits.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | 分析 API, Projects API |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | - | API-only |

## 认证方式

- **类型**: API Key
- **Parameter**: `key={api_key}` in query string
- **Get key**: My Profile > API in SEMrush dashboard

## 常见代理操作

### Domain 概览

```bash
GET https://api.semrush.com/?type=domain_ranks&key={api_key}&export_columns=Db,Dn,Rk,Or,Ot,Oc,Ad,At,Ac&domain=example.com
```

### 自然搜索关键词

```bash
GET https://api.semrush.com/?type=domain_organic&key={api_key}&export_columns=Ph,Po,Pp,Pd,Nq,Cp,Ur,Tr,Tc,Co,Nr&domain=example.com&database=us&display_limit=100
```

### 关键词概览

```bash
GET https://api.semrush.com/?type=phrase_all&key={api_key}&export_columns=Ph,Nq,Cp,Co,Nr&phrase=keyword&database=us
```

### Related 关键词

```bash
GET https://api.semrush.com/?type=phrase_related&key={api_key}&export_columns=Ph,Nq,Cp,Co,Nr,Td&phrase=keyword&database=us&display_limit=50
```

### 关键词 difficulty

```bash
GET https://api.semrush.com/?type=phrase_kdi&key={api_key}&export_columns=Ph,Kd&phrase=keyword&database=us
```

### 反向链接概览

```bash
GET https://api.semrush.com/?type=backlinks_overview&key={api_key}&target=example.com&target_type=root_domain
```

### 反向链接列表

```bash
GET https://api.semrush.com/?type=backlinks&key={api_key}&target=example.com&target_type=root_domain&export_columns=source_url,source_title,target_url,anchor&display_limit=100
```

### Competitors

```bash
GET https://api.semrush.com/?type=domain_organic_organic&key={api_key}&export_columns=Dn,Cr,Np,Or,Ot,Oc,Ad&domain=example.com&database=us&display_limit=20
```

## Response Format

Responses are CSV by default. Add `&export_escape=1` for proper escaping.

## Export Columns

### Domain 报告
- `Db` - Database
- `Dn` - Domain
- `Rk` - Rank
- `Or` - Organic 关键词
- `Ot` - Organic traffic
- `Oc` - Organic cost

### 关键词 报告
- `Ph` - Phrase/关键词
- `Nq` - 搜索 volume
- `Cp` - CPC
- `Co` - Competition
- `Kd` - 关键词 difficulty
- `Nr` - Number of results

### Backlinks
- `source_url` - Linking page
- `target_url` - Target page
- `anchor` - Anchor text
- `source_title` - Page title

## Databases

Use country code: `us`, `uk`, `de`, `fr`, `ca`, `au`, etc.

## 适用场景

- 关键词 调研
- Competitive 分析
- Backlink 分析
- Site audits
- Rank 跟踪
- Content gap 分析

## 速率限制

- Varies by plan (10-30K units/day)
- Each API call costs units

## 相关技能

- seo-audit
- programmatic-seo
- content-strategy
- competitor-alternatives
