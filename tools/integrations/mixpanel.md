# Mixpanel

产品 分析 平台 for 跟踪 user behavior and retention.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Ingestion API, Query API, Data Export |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | JavaScript, iOS, Android, Python, etc. |

## 认证方式

- **Ingestion**: Project token (public)
- **Query API**: Service 账户 (username:secret as Basic auth)
- **Export**: API Secret

## 常见代理操作

### 跟踪事件 (Ingestion API)

```bash
POST https://api.mixpanel.com/track

{
  "event": "signup_completed",
  "properties": {
    "token": "{project_token}",
    "distinct_id": "user_123",
    "plan": "pro",
    "time": 1705312800
  }
}
```

### Set user profile

```bash
POST https://api.mixpanel.com/engage

{
  "$token": "{project_token}",
  "$distinct_id": "user_123",
  "$set": {
    "$email": "user@example.com",
    "$name": "John Doe",
    "plan": "pro"
  }
}
```

### Query events (Query API)

```bash
POST https://mixpanel.com/api/2.0/insights

{
  "project_id": {project_id},
  "bookmark_id": null,
  "params": {
    "events": [{"event": "signup_completed"}],
    "time_range": {
      "from_date": "2024-01-01",
      "to_date": "2024-01-31"
    }
  }
}
```

### Get funnel data

```bash
GET https://mixpanel.com/api/2.0/funnels?funnel_id={funnel_id}&from_date=2024-01-01&to_date=2024-01-31
```

### Export raw events

```bash
GET https://data.mixpanel.com/api/2.0/export?from_date=2024-01-01&to_date=2024-01-01
```

### Get retention data

```bash
GET https://mixpanel.com/api/2.0/retention?from_date=2024-01-01&to_date=2024-01-31&retention_type=birth&born_event=signup_completed
```

## JavaScript SDK

```javascript
// Initialize
mixpanel.init('YOUR_TOKEN');

// Identify user
mixpanel.identify('user_123');

// Set user properties
mixpanel.people.set({
  '$email': 'user@example.com',
  'plan': 'pro'
});

// Track event
mixpanel.track('Feature Used', {
  'feature_name': 'export'
});
```

## 关键概念

- **Events** - User actions (signup, purchase, etc.)
- **Properties** - Attributes on events
- **User Profiles** - Persistent 用户数据
- **Cohorts** - Saved user segments
- **Funnels** - Conversion sequences
- **Retention** - User return patterns

## 适用场景

- 跟踪 产品 usage events
- Analyzing conversion funnels
- Measuring feature adoption
- Retention 分析
- User segmentation

## 速率限制

- Ingestion: No hard limit (batch recommended)
- Query API: Varies by plan

## 相关技能

- 分析-跟踪
- ab-test-配置方式
- onboarding-cro
