# WordPress

Content management system for blogs and websites.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API (WP REST API) |
| MCP | - | 不可用 |
| CLI | ✓ | WP-CLI for server-side management |
| SDK | ✓ | Various client libraries |

## 认证方式

- **类型**: Application Password, JWT, or OAuth
- **请求头**: `Authorization: Basic {base64(username:app_password)}`
- **配置方式**: Users > Your Profile > Application Passwords

## 常见代理操作

### List posts

```bash
GET https://example.com/wp-json/wp/v2/posts?per_page=10

Authorization: Basic {base64(username:app_password)}
```

### Get post

```bash
GET https://example.com/wp-json/wp/v2/posts/{post_id}

Authorization: Basic {base64(username:app_password)}
```

### Create post

```bash
POST https://example.com/wp-json/wp/v2/posts

Authorization: Basic {base64(username:app_password)}

{
  "title": "Post Title",
  "content": "<p>Post content here</p>",
  "status": "draft",
  "categories": [1],
  "tags": [5, 6]
}
```

### Update post

```bash
PUT https://example.com/wp-json/wp/v2/posts/{post_id}

Authorization: Basic {base64(username:app_password)}

{
  "title": "Updated Title",
  "status": "publish"
}
```

### List 页面

```bash
GET https://example.com/wp-json/wp/v2/pages?per_page=20

Authorization: Basic {base64(username:app_password)}
```

### List categories

```bash
GET https://example.com/wp-json/wp/v2/categories
```

### Create category

```bash
POST https://example.com/wp-json/wp/v2/categories

{
  "name": "Category Name",
  "slug": "category-name"
}
```

### Upload media

```bash
POST https://example.com/wp-json/wp/v2/media

Authorization: Basic {base64(username:app_password)}
Content-Disposition: attachment; filename="image.jpg"
Content-Type: image/jpeg

[binary image data]
```

### List 用户

```bash
GET https://example.com/wp-json/wp/v2/users

Authorization: Basic {base64(username:app_password)}
```

## WP-CLI Commands

```bash
# List posts
wp post list --post_type=post --post_status=publish

# Create post
wp post create --post_title="Title" --post_content="Content" --post_status=publish

# Update post
wp post update 123 --post_title="New Title"

# Export database
wp db export backup.sql

# Search/replace in database
wp search-replace 'old-domain.com' 'new-domain.com'

# Install plugin
wp plugin install yoast-seo --activate

# Update plugins
wp plugin update --all
```

## Post Statuses

- `publish` - Live on site
- `draft` - Not published
- `pending` - Awaiting review
- `private` - Private post
- `future` - Scheduled
- `trash` - In trash

## 常见 Endpoints

| Endpoint | Resource |
|----------|----------|
| `/wp/v2/posts` | Blog posts |
| `/wp/v2/pages` | Pages |
| `/wp/v2/media` | Images/files |
| `/wp/v2/categories` | Categories |
| `/wp/v2/tags` | Tags |
| `/wp/v2/users` | Users |
| `/wp/v2/comments` | Comments |

## 适用场景

- Blog content 管理
- Page updates
- Media 管理
- Site configuration
- Plugin/theme 管理

## 速率限制

- No default limits
- Server/host dependent

## 相关技能

- content-strategy
- seo-audit
- programmatic-seo
