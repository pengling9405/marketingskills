# Lemlist

Cold email outreach 平台 with personalization and 广告活动 management.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for 广告活动, leads, activities, webhooks |
| MCP | - | 不可用 |
| CLI | [✓](../clis/lemlist.js) | Zero-dependency Node.js CLI |
| SDK | - | API-only |

## 认证方式

- **类型**: Basic Auth (empty username, API key as password)
- **请求头**: `Authorization: Basic base64(:api_key)`
- **Env var**: `LEMLIST_API_KEY`
- **Get key**: [Lemlist Settings > Integrations](https://app.lemlist.com/settings/integrations)

## 常见代理操作

### 列出广告活动

```bash
node tools/clis/lemlist.js campaigns list --offset 0 --limit 20
```

### Get 广告活动 details and stats

```bash
# Get campaign
node tools/clis/lemlist.js campaigns get --id cam_abc123

# Get campaign stats
node tools/clis/lemlist.js campaigns stats --id cam_abc123

# Export campaign data
node tools/clis/lemlist.js campaigns export --id cam_abc123
```

### Manage leads in a 广告活动

```bash
# List leads
node tools/clis/lemlist.js leads list --campaign-id cam_abc123

# Add a lead
node tools/clis/lemlist.js leads add --campaign-id cam_abc123 --email john@example.com --first-name John --last-name Doe --company "Example Inc"

# Get lead details
node tools/clis/lemlist.js leads get --campaign-id cam_abc123 --email john@example.com

# Remove a lead
node tools/clis/lemlist.js leads delete --campaign-id cam_abc123 --email john@example.com
```

### Manage unsubscribes

```bash
# List unsubscribed emails
node tools/clis/lemlist.js unsubscribes list

# Add to unsubscribe list
node tools/clis/lemlist.js unsubscribes add --email john@example.com

# Remove from unsubscribe list
node tools/clis/lemlist.js unsubscribes delete --email john@example.com
```

### View activities

```bash
# All activities
node tools/clis/lemlist.js activities list

# Filter by campaign and type
node tools/clis/lemlist.js activities list --campaign-id cam_abc123 --type emailsOpened
```

### Manage webhooks

```bash
# List hooks
node tools/clis/lemlist.js hooks list

# Create a webhook
node tools/clis/lemlist.js hooks create --target-url https://example.com/webhook --event emailsOpened

# Delete a webhook
node tools/clis/lemlist.js hooks delete --id hook_123
```

### Team info

```bash
node tools/clis/lemlist.js team info
```

## 速率限制

- API 速率限制 vary by plan
- Recommended: stay under 10 requests/second

## Use Cases

- **Link building outreach**: Add prospects to 广告活动 for backlink requests
- **广告活动 management**: Monitor open/reply rates across outreach 广告活动
- **Lead management**: Add, remove, and track leads across 广告活动
- **Webhook integration**: Get real-time notifications for email events
