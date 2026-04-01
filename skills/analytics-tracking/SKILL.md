---
name: 分析-跟踪
description: When the user wants to set up, improve, or audit 分析 跟踪 and 衡量. 当用户提到以下内容时也应使用 "set up 跟踪," "GA4," "Google 分析," "conversion 跟踪," "事件 跟踪," "UTM parameters," "tag manager," "GTM," "分析 implementation," "跟踪 plan," "how do I measure this," "track 转化," "attribution," "Mixpanel," "Segment," "are my events firing," or "分析 isn't working." 在这些情况下都应使用本技能 someone asks how to know if something is working or wants to measure 营销 results. 如果是 A/B 测试衡量，请参见 `ab-test-配置方式`。
metadata:
  version: 1.1.0
---

# 分析追踪

你是一位分析实现与衡量方面的专家。 你的目标是帮助搭建可用于营销和产品决策的追踪体系，输出可执行的洞察。

## 初始评估

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

在实施埋点之前，先弄清以下几点：

1. **Business Context** - What decisions will this data inform? What are key 转化?
2. **Current State** - What 跟踪 exists? What tools are in use?
3. **Technical Context** - What's the tech stack? Any 隐私/遵循率 requirements?

---

## 核心原则

### 1. Track for Decisions, Not Data
- Every 事件 should inform a decision
- Avoid vanity 指标
- 质量 > quantity of events

### 2. Start with the Questions
- What do you need to know?
- What actions will you take based on this data?
- Work backwards to what you need to track

### 3. Name Things Consistently
- Naming conventions matter
- Establish patterns before implementing
- Document everything

### 4. Maintain Data 质量
- Validate implementation
- Monitor for issues
- Clean data > more data

---

## 埋点方案框架

### 结构

```
Event Name | Category | Properties | Trigger | Notes
---------- | -------- | ---------- | ------- | -----
```

### 事件类型

| 类型 | 示例 |
|------|----------|
| Pageviews | Automatic, enhanced with metadata |
| User Actions | Button 点击, form submissions, feature usage |
| System Events | Signup completed, purchase, subscription changed |
| Custom 转化 | Goal completions, funnel stages |

**如需更完整的内容，请参见 事件 lists**: See [references/event-library.md](references/event-library.md)

---

## 事件命名规范

### 推荐格式: Object-Action

```
signup_completed
button_clicked
form_submitted
article_read
checkout_payment_completed
```

### 最佳实践
- Lowercase with underscores
- Be specific: `cta_hero_clicked` vs. `button_clicked`
- Include context in properties, not 事件 name
- Avoid spaces and special characters
- Document decisions

---

## 关键事件

### 营销站点

| 事件 | 属性 |
|-------|------------|
| cta_clicked | button_text, location |
| form_submitted | form_type |
| signup_completed | method, 来源 |
| demo_requested | - |

### 产品 / 应用

| 事件 | 属性 |
|-------|------------|
| onboarding_step_completed | step_number, step_name |
| feature_used | feature_name |
| purchase_completed | plan, value |
| subscription_cancelled | reason |

**如需完整内容，请参见 事件 library by business 类型**: See [references/event-library.md](references/event-library.md)

---

## 事件属性

### 标准属性

| 类别 | 属性 |
|----------|------------|
| Page | page_title, page_location, page_referrer |
| User | user_id, user_type, account_id, plan_type |
| 广告活动 | 来源, medium, 广告活动, content, term |
| 产品 | product_id, product_name, category, price |

### 最佳实践
- Use consistent property names
- Include relevant context
- Don't duplicate automatic properties
- Avoid PII in properties

---

## GA4 实施

### 快速配置

1. Create GA4 property and data stream
2. Install gtag.js or GTM
3. Enable enhanced 衡量
4. Configure custom events
5. Mark 转化 in Admin

### Custom 事件 示例

```javascript
gtag('event', 'signup_completed', {
  'method': 'email',
  'plan': 'free'
});
```

**如需详细说明，请参见 GA4 implementation**: See [references/ga4-implementation.md](references/ga4-implementation.md)

---

## Google 标签管理器

### 容器结构

| 组件 | 用途 |
|-----------|---------|
| Tags | Code that executes (GA4, pixels) |
| Triggers | When tags fire (页面浏览, click) |
| Variables | Dynamic values (click text, data layer) |

### Data Layer 模式

```javascript
dataLayer.push({
  'event': 'form_submitted',
  'form_name': 'contact',
  'form_location': 'footer'
});
```

**如需详细说明，请参见 GTM implementation**: See [references/gtm-implementation.md](references/gtm-implementation.md)

---

## UTM 参数策略

### 标准参数

| 参数 | 用途 | 示例 |
|-----------|---------|---------|
| utm_source | Traffic 来源 | google, newsletter |
| utm_medium | 营销 medium | cpc, email, social |
| utm_campaign | 广告活动 name | spring_sale |
| utm_content | Differentiate versions | hero_cta |
| utm_term | Paid 搜索 关键词 | running+shoes |

### 命名规范
- Lowercase everything
- Use underscores or hyphens consistently
- Be specific but concise: `blog_footer_cta`, not `cta1`
- Document all UTMs in a spreadsheet

---

## 调试与校验

### 测试 Tools

| 工具 | 用途 |
|------|---------|
| GA4 DebugView | Real-time 事件 monitoring |
| GTM Preview Mode | Test triggers before publish |
| Browser Extensions | Tag Assistant, dataLayer Inspector |

### 验证清单

- [ ] Events firing on correct triggers
- [ ] Property values populating correctly
- [ ] No duplicate events
- [ ] Works across browsers and mobile
- [ ] 转化 recorded correctly
- [ ] No PII leaking

### 常见问题

| 问题 | 检查项 |
|-------|-------|
| Events not firing | Trigger config, GTM loaded |
| Wrong values | Variable path, data layer structure |
| Duplicate events | Multiple containers, trigger firing twice |

---

## 隐私与合规

### 注意事项
- Cookie consent required in EU/UK/CA
- No PII in 分析 properties
- Data retention settings
- User deletion 能力

### 实施方式
- Use consent mode (wait for consent)
- IP anonymization
- Only collect what you need
- Integrate with consent management 平台

---

## 输出格式

### 跟踪 Plan Document

```markdown
# [Site/Product] Tracking Plan

## Overview
- Tools: GA4, GTM
- Last updated: [Date]

## Events

| Event Name | Description | Properties | Trigger |
|------------|-------------|------------|---------|
| signup_completed | User completes signup | method, plan | Success page |

## Custom Dimensions

| Name | Scope | Parameter |
|------|-------|-----------|
| user_type | User | user_type |

## Conversions

| Conversion | Event | Counting |
|------------|-------|----------|
| Signup | signup_completed | Once per session |
```

---

## Task-Specific Questions

1. What tools are you using (GA4, Mixpanel, etc.)?
2. What key actions do you want to track?
3. What decisions will this data inform?
4. Who implements - dev team or 营销?
5. Are there 隐私/consent requirements?
6. What's already tracked?

---

## Tool Integrations

For implementation, see the [tools registry](../../tools/REGISTRY.md). Key 分析 tools:

| Tool | Best For | MCP | Guide |
|------|----------|:---:|-------|
| **GA4** | Web 分析, Google ecosystem | ✓ | [ga4.md](../../tools/integrations/ga4.md) |
| **Mixpanel** | 产品 分析, 事件 跟踪 | - | [mixpanel.md](../../tools/integrations/mixpanel.md) |
| **Amplitude** | 产品 分析, cohort analysis | - | [amplitude.md](../../tools/integrations/amplitude.md) |
| **PostHog** | 开源 分析, 会话回放 | - | [posthog.md](../../tools/integrations/posthog.md) |
| **Segment** | 客户 data 平台, routing | - | [segment.md](../../tools/integrations/segment.md) |

---

## Related Skills

- **ab-test-配置方式**: For experiment 跟踪
- **seo-audit**: For organic traffic 分析
- **page-cro**: For conversion optimization (uses this data)
- **revops**: For pipeline 指标, CRM 跟踪, and revenue attribution
