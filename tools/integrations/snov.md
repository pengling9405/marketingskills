# Snov.io

用于外联的邮箱查找、验证和 drip campaign 平台。

## 能力

| 集成方式 | 可用性 | 说明 |
|-------------|--------|------|
| API | ✓ | 提供邮箱查找、验证、prospect、drip campaign 的 REST API |
| MCP | - | 不可用 |
| CLI | [✓](../clis/snov.js) | 零依赖 Node.js CLI |
| SDK | - | 仅提供 API |

## 认证

- **类型**：OAuth2 client credentials
- **流程**：向 `/oauth/access_token` 发起 POST，并附带 `client_id` + `client_secret`
- **环境变量**：`SNOV_CLIENT_ID`、`SNOV_CLIENT_SECRET`
- **获取方式**：[Snov.io > Integration > API](https://app.snov.io/integration/api)

CLI 会自动处理 token 获取。

## 常见 Agent 操作

### 按域名搜索邮箱

```bash
node tools/clis/snov.js domain search --domain example.com --type all --limit 10
```

### 查找某个具体联系人的邮箱

```bash
node tools/clis/snov.js email find --domain example.com --first-name John --last-name Doe
```

### 验证邮箱

```bash
node tools/clis/snov.js email verify --email john@example.com
```

### 按邮箱查找 prospect

```bash
node tools/clis/snov.js prospect find --email john@example.com
```

### 把 prospect 加入列表

```bash
node tools/clis/snov.js prospect add --email john@example.com --first-name John --last-name Doe --list-id 12345
```

### 管理 prospect 列表

```bash
# 列出所有列表
node tools/clis/snov.js lists list

# 获取列表中的 prospect
node tools/clis/snov.js lists prospects --id 12345 --page 1 --per-page 50
```

### 检查域名技术栈

```bash
node tools/clis/snov.js technology check --domain example.com
```

### 管理 drip campaign

```bash
# 列出 Campaign
node tools/clis/snov.js drips list

# 获取 Campaign 详情
node tools/clis/snov.js drips get --id 12345

# 把 prospect 加入 drip campaign
node tools/clis/snov.js drips add-prospect --id 12345 --email john@example.com
```

## 限流

- 限流随套餐不同而变化
- OAuth token 会在一定时间后过期；CLI 会自动处理刷新

## 使用场景

- **链接建设**：查找联系人并运行自动化 drip outreach
- **商机挖掘**：构建和管理 prospect 列表
- **技术研究**：查看目标域名使用了什么技术栈
- **邮箱验证**：发送前清洗列表
