# Webflow

Visual web design and CMS 平台 for 营销 sites.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for sites, CMS, forms |
| MCP | - | 不可用 |
| CLI | ✓ | Webflow CLI for devlink and apps |
| SDK | ✓ | Official SDK for Node.js |

## 认证方式

- **类型**: API Token (Site token or OAuth)
- **请求头**: `Authorization: Bearer {api_token}`
- **获取令牌**： Site Settings > Integrations > API Access

## 常见代理操作

### List sites

```bash
GET https://api.webflow.com/v2/sites

Authorization: Bearer {api_token}
```

### Get site

```bash
GET https://api.webflow.com/v2/sites/{site_id}

Authorization: Bearer {api_token}
```

### List collections

```bash
GET https://api.webflow.com/v2/sites/{site_id}/collections

Authorization: Bearer {api_token}
```

### List collection items

```bash
GET https://api.webflow.com/v2/collections/{collection_id}/items

Authorization: Bearer {api_token}
```

### Get collection item

```bash
GET https://api.webflow.com/v2/collections/{collection_id}/items/{item_id}

Authorization: Bearer {api_token}
```

### Create collection item

```bash
POST https://api.webflow.com/v2/collections/{collection_id}/items

Authorization: Bearer {api_token}

{
  "fieldData": {
    "name": "Item Name",
    "slug": "item-name",
    "custom-field": "value"
  }
}
```

### Update collection item

```bash
PATCH https://api.webflow.com/v2/collections/{collection_id}/items/{item_id}

Authorization: Bearer {api_token}

{
  "fieldData": {
    "custom-field": "new value"
  }
}
```

### Publish collection items

```bash
POST https://api.webflow.com/v2/collections/{collection_id}/items/publish

Authorization: Bearer {api_token}

{
  "itemIds": ["item_id_1", "item_id_2"]
}
```

### List form submissions

```bash
GET https://api.webflow.com/v2/sites/{site_id}/forms/{form_id}/submissions

Authorization: Bearer {api_token}
```

### Publish site

```bash
POST https://api.webflow.com/v2/sites/{site_id}/publish

Authorization: Bearer {api_token}

{
  "publishToWebflowSubdomain": true,
  "publishToCustomDomains": true
}
```

## Node.js SDK

```javascript
const Webflow = require('webflow-api');

const webflow = new Webflow({ token: 'api_token' });

// List sites
const sites = await webflow.sites.list();

// Get collection items
const items = await webflow.collections.items.listItems(collectionId);

// Create item
const item = await webflow.collections.items.createItem(collectionId, {
  fieldData: {
    name: 'New Item',
    slug: 'new-item'
  }
});
```

## CLI Commands

```bash
# Install
npm install -g @webflow/webflow-cli

# Login
webflow login

# Initialize devlink
webflow devlink init

# Sync components
webflow devlink sync
```

## CMS Structure

- **Collections** - Content types (like blog posts, team members)
- **Items** - Individual entries in a collection
- **Fields** - Data fields on items

## 常见 Field Types

- `PlainText` - Simple text
- `RichText` - Formatted content
- `Image` - Image upload
- `Link` - URL or page 参考
- `Reference` - Link to another collection
- `Multi-Reference` - Multiple collection links
- `Switch` - Boolean toggle
- `Number` - Numeric value
- `Date` - Date/time

## 适用场景

- 营销 site CMS 管理
- Blog/content publishing
- Form submission handling
- Automated content updates
- Programmatic SEO pages

## 速率限制

- 60 requests/minute (general)
- 10 requests/minute (publishing)

## 相关技能

- programmatic-seo
- content-strategy
- page-cro
