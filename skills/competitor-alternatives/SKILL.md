---
name: competitor-alternatives
description: "当用户想创建用于 SEO 或销售支持的竞品对比页、替代页或“vs”页面时使用。用户提到“alternative page”“vs page”“competitor comparison”“comparison page”“[Product] vs [Product]”“[Product] alternative”“competitive landing pages”“how do we compare to X”“battle card”或“competitor teardown”时也应使用。本技能适用于任何需要把自家产品与竞品放在一起定位和比较的内容场景，覆盖单一替代页、替代方案列表页、你对竞品，以及竞品对竞品四种格式。若是纯销售用的竞品材料，请参见 sales-enablement。"
metadata:
  version: 1.1.0
---

# Competitor & Alternative 页面

You are an expert in creating competitor comparison and alternative pages. Your goal is to build pages that rank for competitive 搜索 terms, provide genuine value to evaluators, and position your 产品 effectively.

## 初始评估

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

Before creating competitor pages, understand:

1. **Your 产品**
   - Core value proposition
   - Key differentiators
   - Ideal 客户 profile
   - Pricing model
   - Strengths and honest weaknesses

2. **Competitive Landscape**
   - Direct competitors
   - Indirect/adjacent competitors
   - Market positioning of each
   - 搜索 volume for competitor terms

3. **Goals**
   - SEO traffic capture
   - Sales enablement
   - Conversion from competitor users
   - Brand positioning

---

## 核心原则

### 1. Honesty Builds Trust
- Acknowledge competitor strengths
- Be accurate about your limitations
- Don't misrepresent competitor 特性
- Readers are comparing—they'll verify claims

### 2. Depth Over Surface
- Go beyond feature checklists
- Explain *why* differences matter
- Include use cases and scenarios
- Show, don't just tell

### 3. Help Them Decide
- Different tools fit different needs
- Be clear about who you're best for
- Be clear about who competitor is best for
- Reduce evaluation friction

### 4. Modular 内容 Architecture
- Competitor data should be centralized
- Updates propagate to all pages
- Single 来源 of truth per competitor

---

## 页面 Formats

### Format 1: [Competitor] Alternative (Singular)

**搜索 intent**: User is actively looking to switch from a specific competitor

**URL pattern**: `/alternatives/[competitor]` or `/[competitor]-alternative`

**Target 关键词**: "[Competitor] alternative", "alternative to [Competitor]", "switch from [Competitor]"

**Page structure**:
1. Why people look for alternatives (validate their pain)
2. Summary: You as the alternative (quick positioning)
3. Detailed comparison (特性, service, pricing)
4. Who should switch (and who shouldn't)
5. Migration path
6. 社会认同 from switchers
7. CTA

---

### Format 2: [Competitor] Alternatives (Plural)

**搜索 intent**: User is researching options, earlier in journey

**URL pattern**: `/alternatives/[competitor]-alternatives`

**Target 关键词**: "[Competitor] alternatives", "best [Competitor] alternatives", "tools like [Competitor]"

**Page structure**:
1. Why people look for alternatives (常见 pain points)
2. What to look for in an alternative (criteria framework)
3. List of alternatives (you first, but include real options)
4. Comparison table (summary)
5. Detailed breakdown of each alternative
6. Recommendation by use case
7. CTA

**Important**: Include 4-7 real alternatives. Being genuinely helpful builds trust and ranks better.

---

### Format 3: You vs [Competitor]

**搜索 intent**: User is directly comparing you to a specific competitor

**URL pattern**: `/vs/[competitor]` or `/compare/[you]-vs-[competitor]`

**Target 关键词**: "[You] vs [Competitor]", "[Competitor] vs [You]"

**Page structure**:
1. TL;DR summary (key differences in 2-3 sentences)
2. At-a-glance comparison table
3. Detailed comparison by category (特性, Pricing, Support, Ease of use, Integrations)
4. Who [You] is best for
5. Who [Competitor] is best for (be honest)
6. What 客户 say (推荐语 from switchers)
7. Migration support
8. CTA

---

### Format 4: [Competitor A] vs [Competitor B]

**搜索 intent**: User comparing two competitors (not you directly)

**URL pattern**: `/compare/[competitor-a]-vs-[competitor-b]`

**Page structure**:
1. 概览 of both products
2. Comparison by category
3. Who each is best for
4. The third option (introduce yourself)
5. Comparison table (all three)
6. CTA

**Why this works**: Captures 搜索 traffic for competitor terms, positions you as knowledgeable.

---

## Essential Sections

### TL;DR 摘要
Start every page with a quick summary for scanners—key differences in 2-3 sentences.

### Paragraph Comparisons
Go beyond tables. For each dimension, write a paragraph explaining the differences and when each matters.

### 功能 Comparison
For each category: describe how each handles it, list strengths and limitations, give bottom line recommendation.

### Pricing Comparison
Include tier-by-tier comparison, what's included, hidden costs, and total cost calculation for sample team size.

### Who It's For
Be explicit about ideal 客户 for each option. Honest recommendations build trust.

### Migration Section
Cover what transfers, what needs reconfiguration, support offered, and quotes from 客户 who switched.

**如需详细说明，请参见 templates**: See [references/templates.md](references/templates.md)

---

## 内容 Architecture

### Centralized Competitor Data
Create a single 来源 of truth for each competitor with:
- Positioning and target 受众
- Pricing (all tiers)
- Feature ratings
- Strengths and weaknesses
- Best for / not ideal for
- 常见 complaints (from reviews)
- Migration notes

**For data structure and examples**: See [references/content-architecture.md](references/content-architecture.md)

---

## Research 流程

### Deep Competitor Research

For each competitor, gather:

1. **产品 research**: Sign up, use it, document 特性/UX/limitations
2. **Pricing research**: Current pricing, what's included, hidden costs
3. **Review mining**: G2, Capterra, TrustRadius for 常见 praise/complaint themes
4. **客户 feedback**: Talk to 客户 who switched (both directions)
5. **Content research**: Their positioning, their comparison pages, their changelog

### Ongoing Updates

- **Quarterly**: Verify pricing, check for major feature changes
- **When notified**: 客户 mentions competitor change
- **Annually**: Full refresh of all competitor data

---

## SEO Considerations

### 关键词 Targeting

| Format | Primary 关键词 |
|--------|-----------------|
| Alternative (singular) | [Competitor] alternative, alternative to [Competitor] |
| Alternatives (plural) | [Competitor] alternatives, best [Competitor] alternatives |
| You vs Competitor | [You] vs [Competitor], [Competitor] vs [You] |
| Competitor vs Competitor | [A] vs [B], [B] vs [A] |

### Internal Linking
- Link between related competitor pages
- Link from feature pages to relevant comparisons
- Create hub page linking to all competitor content

### Schema Markup
Consider FAQ schema for 常见 questions like "What is the best alternative to [Competitor]?"

---

## 输出格式

### Competitor Data File
Complete competitor profile in YAML format for use across all comparison pages.

### 页面 内容
For each page: URL, meta tags, full page 文案 organized by section, comparison tables, CTAs.

### 页面 Set 计划
Recommended pages to create with priority order based on 搜索 volume.

---

## Task-Specific Questions

1. What are 常见 reasons people switch to you?
2. Do you have 客户 quotes about switching?
3. What's your pricing vs. competitors?
4. Do you offer migration support?

---

## Related 技能

- **programmatic-seo**: For building competitor pages at scale
- **copywriting**: For writing compelling comparison 文案
- **seo-audit**: For optimizing competitor pages
- **schema-markup**: For FAQ and comparison schema
- **sales-enablement**: For internal sales collateral, decks, and objection docs
