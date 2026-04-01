# Strapi

开源 headless CMS with self-hosted option, REST and GraphQL APIs, and customizable admin panel. Targets Strapi 5.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST (default), GraphQL (plugin) |
| MCP | - | No official MCP server |
| CLI | ✓ | `strapi` CLI for project 配置方式, content types, plugins |
| SDK | ✓ | `@strapi/sdk-js`, `@strapi/blocks-react-renderer` |

## 认证方式

- **类型**: API Token or Users & Permissions JWT
- **请求头**: `Authorization: Bearer {api_token}`
- **Tokens**: Create in Settings → API Tokens (full access, read-only, or custom)
- **JWT**: `POST /api/auth/local` with identifier + password returns JWT

## 常见代理操作

### List documents

```bash
GET http://localhost:1337/api/articles?populate=*

Authorization: Bearer {api_token}
```

### Get single document

```bash
GET http://localhost:1337/api/articles/{documentId}?populate=*

Authorization: Bearer {api_token}
```

### Filter and sort

```bash
# Filter by field
GET http://localhost:1337/api/articles?filters[slug][$eq]=my-post

# Multiple filters
GET http://localhost:1337/api/articles?filters[category][name][$eq]=Marketing&filters[publishedAt][$notNull]=true

# Sort
GET http://localhost:1337/api/articles?sort=publishedAt:desc

# Pagination
GET http://localhost:1337/api/articles?pagination[page]=1&pagination[pageSize]=10
```

### Create document

```bash
POST http://localhost:1337/api/articles
Content-Type: application/json
Authorization: Bearer {api_token}

{
  "data": {
    "title": "New Article",
    "slug": "new-article",
    "body": "Article content here",
    "category": "{category_documentId}"
  }
}
```

### Update document

```bash
PUT http://localhost:1337/api/articles/{documentId}
Content-Type: application/json
Authorization: Bearer {api_token}

{
  "data": {
    "title": "Updated Title"
  }
}
```

### Delete document

```bash
DELETE http://localhost:1337/api/articles/{documentId}

Authorization: Bearer {api_token}
```

### Get draft content

```bash
# Strapi 5 uses status parameter (replaces v4 publicationState)
GET http://localhost:1337/api/articles?status=draft

Authorization: Bearer {api_token}
```

Publishing and unpublishing are managed through the Strapi admin panel or Document Service API (server-side). The public REST API does not expose dedicated publish/unpublish endpoints.

### Populate relations and components

```bash
# Populate all relations
GET http://localhost:1337/api/articles?populate=*

# Populate specific relations
GET http://localhost:1337/api/articles?populate[0]=author&populate[1]=category

# Deep populate
GET http://localhost:1337/api/articles?populate[author][populate]=avatar
```

## CLI Commands

```bash
# Create new Strapi project
npx create-strapi@latest my-project

# Start development server
strapi develop

# Build admin panel
strapi build

# Generate content type
strapi generate content-type

# Generate controller
strapi generate controller

# Add GraphQL plugin
npm install @strapi/plugin-graphql
```

## Key Objects

- **Content 类型** — Schema definition (collection 类型 or single 类型)
- **Document** — Content item identified by `documentId` (Strapi 5 pattern)
- **Component** — Reusable field group (e.g., SEO fields, CTA block)
- **Dynamic Zone** — Flexible content area accepting multiple component types
- **Media** — Files managed through the Media Library
- **Locale** — i18n locale for content translation (plugin-based)

## 适用场景

- Self-hosted CMS with full data ownership
- 预算-conscious projects (no per-seat pricing)
- Custom admin panel or plugin requirements
- Teams with DevOps capability
- Projects needing both REST and GraphQL access

## 速率限制

- Self-hosted: No built-in 速率限制 (configure via middleware or reverse proxy)
- Strapi Cloud: Varies by plan
- Recommended: Add rate limiting middleware for production APIs

## 相关技能

- content-strategy (CMS selection, content modeling)
- programmatic-seo (CMS as data 来源 for generated pages)
- site-architecture (URL structure from CMS slugs)
