# AirOps

AI content 平台 for crafting content that wins AI 搜索. Build and execute AI 工作流 (flows) for SEO content generation, data enrichment, and automation.

## 能力概览

| 集成方式 | 是否可用 | 说明 |
|-------------|-----------|-------|
| API | ✓ | Flows, 工作流, Runs |
| MCP | - | 不可用 |
| CLI | ✓ | [airops.js](../clis/airops.js) |
| SDK | - | REST API only |

## 认证方式

- **类型**: API Key + Workspace ID
- **请求头**: `Authorization: Bearer {api_key}`
- **Env vars**: `AIROPS_API_KEY`, `AIROPS_WORKSPACE_ID`
- **Get key**: Settings > API Keys at https://app.airops.com

## 常见代理操作

### List Flows

```bash
GET https://api.airops.com/public_api/v1/workspaces/{workspace_id}/flows
```

### Get Flow Details

```bash
GET https://api.airops.com/public_api/v1/workspaces/{workspace_id}/flows/{flow_id}
```

### Execute a Flow

```bash
POST https://api.airops.com/public_api/v1/workspaces/{workspace_id}/flows/{flow_id}/execute

{
  "inputs": {
    "keyword": "best project management tools",
    "target_audience": "startup founders"
  }
}
```

### List Runs for a Flow

```bash
GET https://api.airops.com/public_api/v1/workspaces/{workspace_id}/flows/{flow_id}/runs
```

### Get Run Status

```bash
GET https://api.airops.com/public_api/v1/workspaces/{workspace_id}/runs/{run_id}
```

### List 工作流

```bash
GET https://api.airops.com/public_api/v1/workspaces/{workspace_id}/workflows
```

### Execute a 工作流

```bash
POST https://api.airops.com/public_api/v1/workspaces/{workspace_id}/workflows/{workflow_id}/execute

{
  "inputs": {
    "topic": "email marketing best practices",
    "content_type": "blog_post"
  }
}
```

## 核心指标

### Flow Data
- `id` - Flow identifier
- `name` - Flow name
- `description` - Flow description
- `status` - Active/inactive status
- `created_at` - Creation timestamp
- `updated_at` - Last modified timestamp

### Run Data
- `id` - Run identifier
- `flow_id` - Parent flow ID
- `status` - pending, running, completed, failed
- `inputs` - Input parameters used
- `outputs` - Generated results
- `started_at` - Run start time
- `completed_at` - Run completion time

## Parameters

### Flow Execution
- `inputs` - JSON object of key-value pairs matching the flow's expected inputs
- Input keys vary per flow (e.g., `keyword`, `topic`, `url`, `target_audience`)

### 工作流 Execution
- `inputs` - JSON object of key-value pairs matching the 工作流's expected inputs

## 适用场景

- Bulk content generation for SEO at scale
- SEO-optimized article creation with AI 工作流
- Data enrichment pipelines for 营销 lists
- 关键词 research automation
- Content optimization and rewriting
- Programmatic SEO page generation
- AI-powered content briefs and outlines

## 速率限制

- 速率限制 vary by plan
- Concurrent execution limits depend on workspace tier
- Check AirOps dashboard for current usage and limits

## 相关技能

- ai-seo
- content-strategy
- programmatic-seo
- copywriting
