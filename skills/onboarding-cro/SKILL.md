---
name: onboarding-cro
description: "当用户想优化 post-signup onboarding、user activation、first-run experience 或 time-to-value 时使用。用户提到“onboarding flow”“activation rate”“user activation”“first-run experience”“empty states”“onboarding checklist”“aha moment”“users aren't activating”“nobody completes setup”“low activation rate”或“users sign up but don't use the product”时也应使用。本技能适用于用户完成注册后没有真正开始使用产品的场景。注册流程优化请参见 signup-flow-cro；持续邮件序列请参见 email-sequence。"
metadata:
  version: 1.1.0
---

# Onboarding CRO

You are an expert in user onboarding and activation. Your goal is to help users reach their "aha moment" as quickly as possible and establish habits that lead to long-term retention.

## 初始评估

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

Before providing recommendations, understand:

1. **产品 Context** - What 类型 of 产品? B2B or B2C? Core value proposition?
2. **Activation Definition** - What's the "aha moment"? What action indicates a user "gets it"?
3. **Current State** - What happens after signup? Where do users drop off?

---

## 核心原则

### 1. Time-to-Value Is Everything
Remove every step between signup and experiencing core value.

### 2. One Goal Per 会话
Focus first session on one successful outcome. Save advanced 特性 for later.

### 3. Do, Don't Show
Interactive > Tutorial. Doing the thing > Learning about the thing.

### 4. Progress Creates Motivation
Show advancement. Celebrate completions. Make the path visible.

---

## Defining Activation

### Find Your Aha Moment

The action that correlates most strongly with retention:
- What do retained users do that churned users don't?
- What's the earliest indicator of future engagement?

**示例 by 产品 类型:**
- Project management: Create first project + add team member
- 分析: Install 跟踪 + see first report
- Design tool: Create first design + export/share
- Marketplace: Complete first transaction

### Activation 指标
- % of signups who reach activation
- Time to activation
- 步骤 to activation
- Activation by cohort/来源

---

## Onboarding Flow 设计

### Immediate Post-Signup (First 30 Seconds)

| Approach | Best For | Risk |
|----------|----------|------|
| 产品-first | Simple products, B2C, mobile | Blank slate overwhelm |
| Guided 配置 | Products needing personalization | Adds friction before value |
| Value-first | Products with demo data | May not feel "real" |

**Whatever you choose:**
- Clear single next action
- No dead ends
- Progress indication if multi-step

### Onboarding Checklist 模式

**适用场景:**
- Multiple 配置 步骤 required
- 产品 has several 特性 to discover
- Self-serve B2B products

**Best practices:**
- 3-7 items (not overwhelming)
- Order by value (most impactful first)
- Start with quick wins
- Progress bar/completion %
- Celebration on completion
- Dismiss option (don't trap users)

### Empty States

Empty states are onboarding opportunities, not dead ends.

**Good empty state:**
- Explains what this area is for
- Shows what it looks like with data
- Clear primary action to add first item
- Optional: Pre-populate with 示例 data

### Tooltips and Guided Tours

**适用场景:** Complex UI, 特性 that aren't self-evident, power 特性 users might miss

**Best practices:**
- Max 3-5 步骤 per tour
- Dismissable at any time
- Don't repeat for returning users

---

## Multi-Channel Onboarding

### 邮件 + In-App Coordination

**Trigger-based emails:**
- Welcome email (immediate)
- Incomplete onboarding (24h, 72h)
- Activation achieved (celebration + next step)
- Feature discovery (days 3, 7, 14)

**Email should:**
- Reinforce in-app actions, not duplicate them
- Drive back to 产品 with specific CTA
- Be personalized based on actions taken

---

## Handling Stalled 用户

### Detection
Define "stalled" criteria (X days inactive, incomplete 配置)

### Re-engagement Tactics

1. **Email sequence** - Reminder of value, address blockers, offer help
2. **In-app recovery** - Welcome back, pick up where left off
3. **Human touch** - For high-value accounts, personal outreach

---

## 衡量

### 核心指标

| 指标 | 说明 |
|--------|-------------|
| Activation rate | % reaching activation 事件 |
| Time to activation | How long to first value |
| Onboarding completion | % completing 配置 |
| Day 1/7/30 retention | Return rate by timeframe |

### Funnel Analysis

Track drop-off at each step:
```
Signup → Step 1 → Step 2 → Activation → Retention
100%      80%       60%       40%         25%
```

Identify biggest drops and focus there.

---

## 输出格式

### Onboarding Audit
For each issue: Finding → Impact → Recommendation → Priority

### Onboarding Flow 设计
- Activation goal
- Step-by-step flow
- Checklist items (if applicable)
- Empty state 文案
- Email sequence triggers
- 指标 plan

---

## 常见 Patterns by 产品 类型

| 产品 类型 | Key 步骤 |
|--------------|-----------|
| B2B SaaS | 配置 wizard → First value action → Team invite → Deep 配置 |
| Marketplace | Complete profile → Browse → First transaction → Repeat loop |
| Mobile App | Permissions → Quick win → Push 配置 → Habit loop |
| Content 平台 | Follow/customize → Consume → Create → Engage |

---

## Experiment Ideas

When recommending experiments, consider tests for:
- Flow simplification (step count, ordering)
- Progress and motivation mechanics
- Personalization by role or goal
- Support and help availability

**如需更完整的内容，请参见 experiment ideas**: See [references/experiments.md](references/experiments.md)

---

## Task-Specific Questions

1. What action most correlates with retention?
2. What happens immediately after signup?
3. Where do users currently drop off?
4. What's your activation rate target?
5. Do you have cohort analysis on successful vs. churned users?

---

## Related 技能

- **signup-flow-cro**: For optimizing the signup before onboarding
- **email-sequence**: For onboarding email series
- **paywall-upgrade-cro**: For converting to paid during/after onboarding
- **ab-test-setup**: For 测试 onboarding changes
