# Amplitude

产品 分析 平台 for user behavior, retention, and experimentation.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | HTTP API for events, User Profile API, Export API |
| MCP | - | 不可用 |
| CLI | - | 不可用 |
| SDK | ✓ | JavaScript, iOS, Android, Python, etc. |

## 认证方式

- **HTTP API**: API Key (public for events)
- **Export/Dashboard API**: API Key + Secret Key

## 常见代理操作

### 跟踪事件

```bash
POST https://api2.amplitude.com/2/httpapi

{
  "api_key": "{api_key}",
  "events": [{
    "user_id": "user_123",
    "event_type": "signup_completed",
    "event_properties": {
      "plan": "pro"
    },
    "user_properties": {
      "email": "user@example.com"
    }
  }]
}
```

### 批量事件

```bash
POST https://api2.amplitude.com/batch

{
  "api_key": "{api_key}",
  "events": [
    {"user_id": "user_1", "event_type": "pageview"},
    {"user_id": "user_2", "event_type": "signup"}
  ]
}
```

### Get 用户 activity

```bash
GET https://amplitude.com/api/2/useractivity?user={user_id}

Authorization: Basic {base64(api_key:secret_key)}
```

### Export events

```bash
GET https://amplitude.com/api/2/export?start=20240101T00&end=20240131T23

Authorization: Basic {base64(api_key:secret_key)}
```

### Get retention data

```bash
GET https://amplitude.com/api/2/retention?e={"event_type":"signup_completed"}&start=20240101&end=20240131

Authorization: Basic {base64(api_key:secret_key)}
```

### Query with SQL (Snowflake)

For Amplitude 客户 with SQL access:
```sql
SELECT event_type, COUNT(*) as count
FROM events
WHERE event_time > '2024-01-01'
GROUP BY event_type
```

## JavaScript SDK

```javascript
// Initialize
amplitude.init('API_KEY');

// Identify user
amplitude.setUserId('user_123');

// Set user properties
const identify = new amplitude.Identify();
identify.set('plan', 'pro');
amplitude.identify(identify);

// Track event
amplitude.track('Feature Used', {
  feature_name: 'export'
});
```

## 关键概念

- **Events** - User actions with properties
- **User Properties** - Persistent user attributes
- **Cohorts** - Behavioral segments
- **Funnels** - Multi-step conversion 分析
- **Retention** - User return patterns
- **Journeys** - User path 分析

## 适用场景

- 跟踪 产品 分析
- Analyzing user funnels
- Cohort analysis and retention
- Experimentation and A/B 测试
- User journey mapping

## 速率限制

- HTTP API: 1000 events/second
- Export API: 360 requests/hour

## 相关技能

- 分析-跟踪
- ab-test-setup
- onboarding-cro
