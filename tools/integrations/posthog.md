# PostHog

开源 产品 分析 with 会话回放 and 功能开关.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Capture API, Query API, 功能开关 API |
| MCP | - | 不可用 |
| CLI | ✓ | `posthog` CLI for local development |
| SDK | ✓ | JavaScript, Python, Ruby, Go, etc. |

## 认证方式

- **类型**: API Key (Personal or Project)
- **请求头**: `Authorization: Bearer {api_key}`
- **用于采集**： Project API Key in payload

## 常见代理操作

### 采集事件

```bash
POST https://app.posthog.com/capture/

{
  "api_key": "{project_api_key}",
  "event": "signup_completed",
  "distinct_id": "user_123",
  "properties": {
    "plan": "pro",
    "$current_url": "https://example.com/signup"
  }
}
```

### 批量事件

```bash
POST https://app.posthog.com/batch/

{
  "api_key": "{project_api_key}",
  "batch": [
    {"event": "pageview", "distinct_id": "user_1"},
    {"event": "signup", "distinct_id": "user_2"}
  ]
}
```

### 按 distinct_id 获取用户

```bash
GET https://app.posthog.com/api/projects/{project_id}/persons/?distinct_id=user_123

Authorization: Bearer {api_key}
```

### 查询事件（HogQL）

```bash
POST https://app.posthog.com/api/projects/{project_id}/query/

{
  "query": {
    "kind": "HogQLQuery",
    "query": "SELECT event, count() FROM events WHERE timestamp > now() - interval 7 day GROUP BY event ORDER BY count() DESC LIMIT 10"
  }
}
```

### 获取功能开关值

```bash
POST https://app.posthog.com/decide?v=3

{
  "api_key": "{project_api_key}",
  "distinct_id": "user_123"
}
```

### 获取洞察

```bash
GET https://app.posthog.com/api/projects/{project_id}/insights/

Authorization: Bearer {api_key}
```

### 获取会话录屏

```bash
GET https://app.posthog.com/api/projects/{project_id}/session_recordings/

Authorization: Bearer {api_key}
```

## JavaScript SDK

```javascript
// Initialize
posthog.init('PROJECT_API_KEY', {
  api_host: 'https://app.posthog.com'
});

// Identify user
posthog.identify('user_123', {
  email: 'user@example.com',
  plan: 'pro'
});

// Track event
posthog.capture('signup_completed', {
  method: 'email'
});

// Check feature flag
if (posthog.isFeatureEnabled('new-pricing')) {
  // Show new pricing
}
```

## 核心特性

- **事件 跟踪** - 产品 分析
- **会话回放** - Watch user sessions
- **功能开关** - Control feature rollout
- **A/B 测试** - Built-in experiments
- **HogQL** - SQL-like query language
- **Self-hostable** - Run on your infrastructure

## 适用场景

- 产品 分析 with 隐私 focus
- 会话回放 for UX insights
- Feature flag 管理
- Self-hosted 分析 needs
- 开源 requirements

## 速率限制

- Cloud: 10,000 events/second
- Self-hosted: Unlimited

## 相关技能

- 分析-跟踪
- ab-test-setup
- onboarding-cro
