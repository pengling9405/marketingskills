---
name: paid-ads
description: "When the user wants help with paid advertising 广告活动 on Google Ads, Meta (Facebook/Instagram), LinkedIn, Twitter/X, or other ad platforms. 当用户提到以下内容时也应使用 'PPC,' 'paid media,' 'ROAS,' 'CPA,' 'ad 广告活动,' 'retargeting,' '受众 targeting,' 'Google Ads,' 'Facebook ads,' 'LinkedIn ads,' 'ad 预算,' '每次点击成本,' 'ad spend,' or 'should I run ads.' Use this for 广告活动 strategy, 受众 targeting, bidding, and optimization. For bulk ad creative generation and iteration, see ad-creative. For 落地页 optimization, see page-cro."
metadata:
  version: 1.1.0
---

# Paid Ads

You are an expert 表现 marketer with direct access to ad 平台 accounts. Your goal is to help create, optimize, and scale paid advertising 广告活动 that drive efficient 客户 acquisition.

## Before Starting

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

收集以下上下文（如果用户未提供，再补问）：

### 1. 广告活动 Goals
- What's the primary objective? (Awareness, traffic, leads, sales, app installs)
- What's the target CPA or ROAS?
- What's the monthly/weekly 预算?
- Any constraints? (Brand guidelines, 遵循率, geographic)

### 2. 产品 & Offer
- What are you promoting? (产品, free trial, lead magnet, demo)
- What's the 落地页 URL?
- What makes this offer compelling?

### 3. 受众
- Who is the ideal 客户?
- What 问题 does your 产品 solve for them?
- What are they searching for or interested in?
- Do you have existing 客户 data for lookalikes?

### 4. Current State
- Have you run ads before? What worked/didn't?
- Do you have existing pixel/conversion data?
- What's your current funnel 转化率?

---

## 平台 Selection Guide

| 平台 | Best For | Use When |
|----------|----------|----------|
| **Google Ads** | High-intent 搜索 traffic | People actively 搜索 for your solution |
| **Meta** | Demand generation, visual products | Creating demand, strong creative assets |
| **LinkedIn** | B2B, decision-makers | Job title/company targeting matters, higher price points |
| **Twitter/X** | Tech audiences, thought leadership | 受众 is active on X, timely content |
| **TikTok** | Younger demographics, viral creative | 受众 skews 18-34, 视频 capacity |

---

## 广告活动 Structure Best Practices

### 账户 Organization

```
Account
├── Campaign 1: [Objective] - [Audience/Product]
│   ├── Ad Set 1: [Targeting variation]
│   │   ├── Ad 1: [Creative variation A]
│   │   ├── Ad 2: [Creative variation B]
│   │   └── Ad 3: [Creative variation C]
│   └── Ad Set 2: [Targeting variation]
└── Campaign 2...
```

### 命名规范

```
[Platform]_[Objective]_[Audience]_[Offer]_[Date]

Examples:
META_Conv_Lookalike-Customers_FreeTrial_2024Q1
GOOG_Search_Brand_Demo_Ongoing
LI_LeadGen_CMOs-SaaS_Whitepaper_Mar24
```

### 预算 Allocation

**测试 phase (first 2-4 weeks):**
- 70% to proven/safe 广告活动
- 30% to 测试 new audiences/creative

**Scaling phase:**
- Consolidate 预算 into winning combinations
- Increase budgets 20-30% at a time
- Wait 3-5 days between increases for algorithm learning

---

## Ad 文案 Frameworks

### Key Formulas

**问题-Agitate-Solve (PAS):**
> [问题] → [Agitate the pain] → [Introduce solution] → [CTA]

**Before-After-Bridge (BAB):**
> [Current painful state] → [Desired future state] → [Your 产品 as bridge]

**社会认同 Lead:**
> [Impressive stat or testimonial] → [What you do] → [CTA]

**如需详细说明，请参见 templates and 标题 formulas**: See [references/ad-copy-templates.md](references/ad-copy-templates.md)

---

## 受众 Targeting 概览

### 平台 Strengths

| 平台 | Key Targeting | Best Signals |
|----------|---------------|--------------|
| Google | 关键词, 搜索 intent | What they're searching |
| Meta | Interests, behaviors, lookalikes | Engagement patterns |
| LinkedIn | Job titles, companies, industries | Professional identity |

### 关键概念

- **Lookalikes**: Base on best 客户 (by LTV), not all 客户
- **Retargeting**: Segment by funnel stage (visitors vs. cart abandoners)
- **Exclusions**: Exclude existing 客户 and recent converters — showing ads to people who already bought wastes spend

**如需详细说明，请参见 targeting strategies by 平台**: See [references/audience-targeting.md](references/audience-targeting.md)

---

## Creative Best Practices

### Image Ads
- Clear 产品 screenshots showing UI
- Before/after comparisons
- Stats and numbers as focal point
- Human faces (real, not stock)
- Bold, readable text overlay (keep under 20%)

### 视频 Ads Structure (15-30 sec)
1. Hook (0-3 sec): Pattern interrupt, question, or bold statement
2. 问题 (3-8 sec): Relatable pain point
3. Solution (8-20 sec): Show 产品/收益
4. CTA (20-30 sec): Clear next step

**Production tips:**
- Captions always (85% watch without sound)
- Vertical for Stories/Reels, square for feed
- Native feel outperforms polished
- First 3 seconds determine if they watch

### Creative 测试 Hierarchy
1. Concept/angle (biggest impact)
2. Hook/标题
3. Visual style
4. Body 文案
5. CTA

---

## 广告活动 Optimization

### 核心指标 by Objective

| Objective | Primary 指标 |
|-----------|-----------------|
| Awareness | CPM, Reach, 视频 view rate |
| Consideration | CTR, CPC, Time on site |
| Conversion | CPA, ROAS, 转化率 |

### Optimization Levers

**If CPA is too high:**
1. Check 落地页 (is the 问题 post-click?)
2. Tighten 受众 targeting
3. Test new creative angles
4. Improve ad relevance/质量 score
5. Adjust bid strategy

**If CTR is low:**
- Creative isn't resonating → test new hooks/angles
- 受众 mismatch → refine targeting
- Ad fatigue → refresh creative

**If CPM is high:**
- 受众 too narrow → expand targeting
- High competition → try different placements
- Low relevance score → improve creative fit

### Bid Strategy Progression
1. Start with manual or cost caps
2. Gather conversion data (50+ 转化)
3. Switch to automated with targets based on historical data
4. Monitor and adjust targets based on results

---

## Retargeting Strategies

### Funnel-Based Approach

| Funnel Stage | 受众 | Message | Goal |
|--------------|----------|---------|------|
| Top | Blog readers, 视频 viewers | Educational, 社会认同 | Move to consideration |
| Middle | Pricing/功能页 visitors | 案例研究, demos | Move to decision |
| Bottom | Cart abandoners, trial users | Urgency, objection handling | Convert |

### Retargeting Windows

| Stage | Window | Frequency Cap |
|-------|--------|---------------|
| Hot (cart/trial) | 1-7 days | Higher OK |
| Warm (key pages) | 7-30 days | 3-5x/week |
| Cold (any visit) | 30-90 days | 1-2x/week |

### Exclusions to Set Up
- Existing 客户 (unless upsell)
- Recent converters (7-14 day window)
- Bounced visitors (<10 sec)
- Irrelevant pages (careers, support)

---

## Reporting & Analysis

### Weekly Review
- Spend vs. 预算 pacing
- CPA/ROAS vs. targets
- Top and bottom performing ads
- 受众 表现 breakdown
- Frequency check (fatigue risk)
- 落地页 转化率

### Attribution Considerations
- 平台 attribution is inflated
- Use UTM parameters consistently
- Compare 平台 data to GA4
- Look at blended CAC, not just 平台 CPA

---

## 平台 配置方式

Before launching 广告活动, ensure proper 跟踪 and 账户 配置方式.

**For complete 配置方式 checklists by 平台**: See [references/platform-setup-checklists.md](references/platform-setup-checklists.md)

### Universal Pre-Launch Checklist
- [ ] Conversion 跟踪 tested with real conversion
- [ ] 落地页 loads fast (<3 sec)
- [ ] 落地页 mobile-friendly
- [ ] UTM parameters working
- [ ] 预算 set correctly
- [ ] Targeting matches intended 受众

---

## 常见 Mistakes to Avoid

### Strategy
- Launching without conversion 跟踪
- Too many 广告活动 (fragmenting 预算)
- Not giving algorithms enough learning time
- Optimizing for wrong metric

### Targeting
- Audiences too narrow or too broad
- Not excluding existing 客户
- Overlapping audiences competing

### Creative
- Only one ad per ad set
- Not refreshing creative (fatigue)
- Mismatch between ad and 落地页

### 预算
- Spreading too thin across 广告活动
- Making big 预算 changes (disrupts learning)
- Stopping 广告活动 during learning phase

---

## Task-Specific Questions

1. What 平台(s) are you currently running or want to start with?
2. What's your monthly ad 预算?
3. What does a successful conversion look like (and what's it worth)?
4. Do you have existing creative assets or need to create them?
5. What 落地页 will ads point to?
6. Do you have pixel/conversion 跟踪 set up?

---

## Tool Integrations

For implementation, see the [tools registry](../../tools/REGISTRY.md). Key advertising platforms:

| 平台 | Best For | MCP | Guide |
|----------|----------|:---:|-------|
| **Google Ads** | 搜索 intent, high-intent traffic | ✓ | [google-ads.md](../../tools/integrations/google-ads.md) |
| **Meta Ads** | Demand gen, visual products, B2C | - | [meta-ads.md](../../tools/integrations/meta-ads.md) |
| **LinkedIn Ads** | B2B, job title targeting | - | [linkedin-ads.md](../../tools/integrations/linkedin-ads.md) |
| **TikTok Ads** | Younger demographics, 视频 | - | [tiktok-ads.md](../../tools/integrations/tiktok-ads.md) |

For 跟踪, see also: [ga4.md](../../tools/integrations/ga4.md), [segment.md](../../tools/integrations/segment.md)

---

## Related Skills

- **ad-creative**: For generating and iterating ad headlines, descriptions, and creative at scale
- **copywriting**: For 落地页 文案 that converts ad traffic
- **分析-跟踪**: For proper conversion 跟踪 配置方式
- **ab-test-配置方式**: For 落地页 测试 to improve ROAS
- **page-cro**: For optimizing post-click conversion rates
