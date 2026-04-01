# Hunter.io

用于外联和链接建设的邮箱查找与验证平台。

## 能力

| 集成方式 | 可用性 | 说明 |
|-------------|--------|------|
| API | ✓ | 提供域名搜索、邮箱查找、验证的 REST API |
| MCP | - | 不可用 |
| CLI | [✓](../clis/hunter.js) | 零依赖 Node.js CLI |
| SDK | - | 仅提供 API |

## 认证

- **类型**：API Key（query 参数）
- **参数**：`api_key={key}`
- **环境变量**：`HUNTER_API_KEY`
- **获取方式**：[Hunter dashboard > API](https://hunter.io/api-keys)

## 常见 Agent 操作

### 查找某个域名下的邮箱

```bash
node tools/clis/hunter.js domain search --domain example.com --limit 10
```

### 查找某个具体联系人的邮箱

```bash
node tools/clis/hunter.js email find --domain example.com --first-name John --last-name Doe
```

### 验证邮箱地址

```bash
node tools/clis/hunter.js email verify --email john@example.com
```

### 统计某个域名可用的邮箱数量

```bash
node tools/clis/hunter.js domain count --domain example.com
```

### 管理线索

```bash
# 列出线索
node tools/clis/hunter.js leads list --limit 20

# 创建线索
node tools/clis/hunter.js leads create --email john@example.com --first-name John --last-name Doe --company "Example Inc"

# 删除线索
node tools/clis/hunter.js leads delete --id 12345
```

### 管理 Campaign

```bash
# 列出 Campaign
node tools/clis/hunter.js campaigns list

# 获取 Campaign 详情
node tools/clis/hunter.js campaigns get --id 12345

# 启动 / 暂停 Campaign
node tools/clis/hunter.js campaigns start --id 12345
node tools/clis/hunter.js campaigns pause --id 12345
```

### 查看账户使用情况

```bash
node tools/clis/hunter.js account info
```

## 限流

- 免费版：每月 25 次搜索、50 次验证
- 付费版配额随套餐提升
- API 限流：10 次请求 / 秒

## 使用场景

- **链接建设**：在目标域名里查找联系人邮箱，方便做 outreach
- **商机挖掘**：基于公司域名构建 lead 列表
- **邮箱验证**：在发送 campaign 前清洗邮箱列表
