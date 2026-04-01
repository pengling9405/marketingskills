# Instantly.ai

Cold email 平台 with built-in email warmup and 广告活动 management at scale.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | REST API for 广告活动, leads, accounts, 分析 |
| MCP | - | 不可用 |
| CLI | [✓](../clis/instantly.js) | Zero-dependency Node.js CLI |
| SDK | - | API-only |

## 认证方式

- **类型**: API Key (query parameter)
- **Parameter**: `api_key={key}`
- **Env var**: `INSTANTLY_API_KEY`
- **Get key**: [Instantly Settings > Integrations > API](https://app.instantly.ai/app/settings/integrations)

## 常见代理操作

### Manage 广告活动

```bash
# List campaigns
node tools/clis/instantly.js campaigns list --limit 20

# Get campaign details
node tools/clis/instantly.js campaigns get --id cam_abc123

# Check campaign 状态
node tools/clis/instantly.js campaigns status --id cam_abc123

# Launch a campaign
node tools/clis/instantly.js campaigns launch --id cam_abc123

# Pause a campaign
node tools/clis/instantly.js campaigns pause --id cam_abc123
```

### Manage leads

```bash
# List leads in a campaign
node tools/clis/instantly.js leads list --campaign-id cam_abc123 --limit 50

# Add a lead
node tools/clis/instantly.js leads add --campaign-id cam_abc123 --email john@example.com --first-name John --last-name Doe --company "Example Inc"

# Delete a lead
node tools/clis/instantly.js leads delete --campaign-id cam_abc123 --email john@example.com

# Check lead 状态
node tools/clis/instantly.js leads status --campaign-id cam_abc123 --email john@example.com
```

### Manage 邮件 accounts

```bash
# List connected accounts
node tools/clis/instantly.js accounts list --limit 20

# Check account 状态
node tools/clis/instantly.js accounts status --account-id me@example.com

# Check warmup 状态
node tools/clis/instantly.js accounts warmup-status --account-id me@example.com
```

### View 分析

```bash
# Campaign analytics
node tools/clis/instantly.js analytics campaign --campaign-id cam_abc123 --start 2024-01-01 --end 2024-01-31

# Step-by-step analytics
node tools/clis/instantly.js analytics steps --campaign-id cam_abc123

# Account-level analytics
node tools/clis/instantly.js analytics account --start 2024-01-01 --end 2024-01-31
```

### Manage blocklist

```bash
# List blocked emails/domains
node tools/clis/instantly.js blocklist list

# Add to blocklist
node tools/clis/instantly.js blocklist add --entries "competitor.com,spam@example.com"
```

## 速率限制

- API 速率限制 vary by plan
- Recommended: stay under 10 requests/second

## Use Cases

- **Link building at scale**: Run large-volume outreach 广告活动 with built-in warmup
- **广告活动 management**: Launch, pause, and monitor cold email 广告活动
- **账户 health**: Monitor email 账户 warmup and deliverability
- **分析**: Track open rates, reply rates, and 广告活动 表现
