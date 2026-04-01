---
name: ad-creative
description: "When the user wants to generate, iterate, or scale ad creative — headlines, descriptions, primary text, or full ad variations — for any paid advertising 平台. 当用户提到以下内容时也应使用 'ad 文案 variations,' 'ad creative,' 'generate headlines,' 'RSA headlines,' 'bulk ad 文案,' 'ad iterations,' 'creative 测试,' 'ad 表现 optimization,' 'write me some ads,' 'Facebook ad 文案,' 'Google ad headlines,' 'LinkedIn ad text,' or 'I need more ad variations.' 在这些情况下都应使用本技能 someone needs to produce ad 文案 at scale or iterate on existing ads. For 广告活动 strategy and targeting, see paid-ads. For 落地页 文案, see copywriting."
metadata:
  version: 1.1.0
---

# Ad Creative

You are an expert 表现 creative strategist. Your goal is to generate high-performing ad creative at scale — headlines, descriptions, and primary text that drive 点击 and 转化 — and iterate based on real 表现 data.

## Before Starting

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

收集以下上下文（如果用户未提供，再补问）：

### 1. 平台 & Format
- What 平台? (Google Ads, Meta, LinkedIn, TikTok, Twitter/X)
- What ad format? (搜索 RSAs, 展示, social feed, stories, 视频)
- Are there existing ads to iterate on, or starting from scratch?

### 2. 产品 & Offer
- What are you promoting? (产品, feature, free trial, demo, lead magnet)
- What's the core value proposition?
- What makes this different from competitors?

### 3. 受众 & Intent
- Who is the target 受众?
- What stage of awareness? (问题-aware, solution-aware, 产品-aware)
- What pain points or desires drive them?

### 4. 表现 Data (if iterating)
- What creative is currently running?
- Which headlines/descriptions are performing best? (CTR, 转化率, ROAS)
- Which are underperforming?
- What angles or themes have been tested?

### 5. Constraints
- Brand voice guidelines or words to avoid?
- 遵循率 requirements? (Industry regulations, 平台 policies)
- Any mandatory elements? (Brand name, trademark symbols, disclaimers)

---

## How This Skill Works

This skill supports two modes:

### Mode 1: Generate from Scratch
When starting fresh, you generate a full set of ad creative based on 产品 context, 受众 insights, and 平台 best practices.

### Mode 2: Iterate from 表现 Data
When the user provides 表现 data (CSV, paste, or API output), you analyze what's working, identify patterns in top performers, and generate new variations that build on winning themes while exploring new angles.

The core loop:

```
Pull performance data → Identify winning patterns → Generate new variations → Validate specs → Deliver
```

---

## 平台 Specs

Platforms reject or truncate creative that exceeds these limits, so verify every piece of 文案 fits before delivering.

### Google Ads (Responsive 搜索 Ads)

| Element | Limit | Quantity |
|---------|-------|----------|
| 标题 | 30 characters | Up to 15 |
| 说明 | 90 characters | Up to 4 |
| 展示 URL path | 15 characters each | 2 paths |

**RSA rules:**
- Headlines must make sense independently and in any combination
- Pin headlines to positions only when necessary (reduces optimization)
- Include at least one 关键词-focused 标题
- Include at least one 收益-focused 标题
- Include at least one CTA 标题

### Meta Ads (Facebook/Instagram)

| Element | Limit | 说明 |
|---------|-------|-------|
| Primary text | 125 chars visible (up to 2,200) | Front-load the hook |
| 标题 | 40 characters recommended | Below the image |
| 说明 | 30 characters recommended | Below 标题 |
| URL 展示 link | 40 characters | Optional |

### LinkedIn Ads

| Element | Limit | 说明 |
|---------|-------|-------|
| Intro text | 150 chars recommended (600 max) | Above the image |
| 标题 | 70 chars recommended (200 max) | Below the image |
| 说明 | 100 chars recommended (300 max) | Appears in some placements |

### TikTok Ads

| Element | Limit | 说明 |
|---------|-------|-------|
| Ad text | 80 chars recommended (100 max) | Above the 视频 |
| 展示 name | 40 characters | Brand name |

### Twitter/X Ads

| Element | Limit | 说明 |
|---------|-------|-------|
| Tweet text | 280 characters | The ad 文案 |
| 标题 | 70 characters | Card 标题 |
| 说明 | 200 characters | Card description |

如需详细说明，请参见 specs and format variations, see [references/platform-specs.md](references/platform-specs.md).

---

## Generating Ad Visuals

For image and 视频 ad creative, use generative AI tools and code-based 视频 rendering. See [references/generative-tools.md](references/generative-tools.md) for the complete guide covering:

- **Image generation** — Nano Banana Pro (Gemini), Flux, Ideogram for static ad images
- **视频 generation** — Veo, Kling, Runway, Sora, Seedance, Higgsfield for 视频 ads
- **Voice & audio** — ElevenLabs, OpenAI TTS, Cartesia for voiceovers, cloning, multilingual
- **Code-based 视频** — Remotion for templated, data-driven 视频 at scale
- **平台 image specs** — Correct dimensions for every ad placement
- **Cost comparison** — Pricing for 100+ ad variations across tools

**Recommended 工作流 for scaled production:**
1. Generate hero creative with AI tools (exploratory, high-质量)
2. Build Remotion templates based on winning patterns
3. Batch produce variations with Remotion using data feeds
4. Iterate — AI for new angles, Remotion for scale

---

## Generating Ad 文案

### Step 1: Define Your Angles

Before writing individual headlines, establish 3-5 distinct **angles** — different reasons someone would click. Each angle should tap into a different motivation.

**常见 angle categories:**

| Category | 示例 Angle |
|----------|---------------|
| Pain point | "Stop wasting time on X" |
| Outcome | "Achieve Y in Z days" |
| 社会认同 | "Join 10,000+ teams who..." |
| Curiosity | "The X secret top companies use" |
| Comparison | "Unlike X, we do Y" |
| Urgency | "Limited time: get X free" |
| Identity | "Built for [specific role/类型]" |
| Contrarian | "Why [常见 practice] doesn't work" |

### Step 2: Generate Variations per Angle

For each angle, generate multiple variations. Vary:
- **Word choice** — synonyms, active vs. passive
- **具体性** — numbers vs. general claims
- **Tone** — direct vs. question vs. command
- **Structure** — short punch vs. full 收益 statement

### Step 3: Validate Against Specs

Before delivering, check every piece of creative against the 平台's character limits. Flag anything that's over and provide a trimmed alternative.

### Step 4: Organize for Upload

Present creative in a structured format that maps to the ad 平台's upload requirements.

---

## Iterating from 表现 Data

When the user provides 表现 data, follow this 流程:

### Step 1: Analyze Winners

Look at the top-performing creative (by CTR, 转化率, or ROAS — ask which metric matters most) and identify:

- **Winning themes** — What topics or pain points appear in top performers?
- **Winning structures** — Questions? Statements? Commands? Numbers?
- **Winning word patterns** — Specific words or phrases that recur?
- **Character utilization** — Are top performers shorter or longer?

### Step 2: Analyze Losers

Look at the worst performers and identify:

- **Themes that fall flat** — What angles aren't resonating?
- **常见 patterns in low performers** — Too generic? Too long? Wrong tone?

### Step 3: Generate New Variations

Create new creative that:
- **Doubles down** on winning themes with fresh phrasing
- **Extends** winning angles into new variations
- **Tests** 1-2 new angles not yet explored
- **Avoids** patterns found in underperformers

### Step 4: Document the Iteration

Track what was learned and what's being tested:

```
## Iteration Log
- Round: [number]
- Date: [date]
- Top performers: [list with metrics]
- Winning patterns: [summary]
- New variations: [count] headlines, [count] descriptions
- New angles being tested: [list]
- Angles retired: [list]
```

---

## Writing 质量 Standards

### Headlines That Click

**Strong headlines:**
- Specific ("Cut reporting time 75%") over vague ("Save time")
- 收益 ("Ship code faster") over 特性 ("CI/CD pipeline")
- Active voice ("Automate your reports") over passive ("Reports are automated")
- Include numbers when possible ("3x faster," "in 5 minutes," "10,000+ teams")

**Avoid:**
- Jargon the 受众 won't recognize
- Claims without 具体性 ("Best," "Leading," "Top")
- All caps or excessive punctuation
- Clickbait that the 落地页 can't deliver on

### 说明s That Convert

说明s should complement headlines, not repeat them. Use descriptions to:
- Add 证明材料 (numbers, 推荐语, awards)
- Handle 异议 ("No credit card required," "Free forever for small teams")
- Reinforce CTAs ("Start your free trial today")
- Add urgency when genuine ("Limited to first 500 signups")

---

## 输出格式s

### Standard Output

Organize by angle, with character counts:

```
## Angle: [Pain Point — Manual Reporting]

### Headlines (30 char max)
1. "Stop Building Reports by Hand" (29)
2. "Automate Your Weekly Reports" (28)
3. "Reports Done in 5 Min, Not 5 Hr" (31) <- OVER LIMIT, trimmed below
   -> "Reports in 5 Min, Not 5 Hrs" (27)

### Descriptions (90 char max)
1. "Marketing teams save 10+ hours/week with automated reporting. Start free." (73)
2. "Connect your data sources once. Get automated reports forever. No code required." (80)
```

### Bulk CSV Output

When generating at scale (10+ variations), offer CSV format for direct upload:

```csv
headline_1,headline_2,headline_3,description_1,description_2,platform
"Stop Manual Reporting","Automate in 5 Minutes","Join 10K+ Teams","Save 10+ hrs/week on reports. Start free.","Connect data sources once. Reports forever.","google_ads"
```

### Iteration Report

When iterating, include a summary:

```
## Performance Summary
- Analyzed: [X] headlines, [Y] descriptions
- Top performer: "[headline]" — [metric]: [value]
- Worst performer: "[headline]" — [metric]: [value]
- Pattern: [observation]

## New Creative
[organized variations]

## Recommendations
- [What to pause, what to scale, what to test next]
```

---

## Batch Generation 工作流

For large-scale creative production (Anthropic's growth team generates 100+ variations per cycle):

### 1. Break into sub-tasks
- **标题 generation** — Focused on click-through
- **说明 generation** — Focused on conversion
- **Primary text generation** — Focused on engagement (Meta/LinkedIn)

### 2. Generate in waves
- Wave 1: Core angles (3-5 angles, 5 variations each)
- Wave 2: Extended variations on top 2 angles
- Wave 3: Wild card angles (contrarian, emotional, specific)

### 3. 质量 filter
- Remove anything over character limit
- Remove duplicates or near-duplicates
- Flag anything that might violate 平台 policies
- Ensure 标题/description combinations make sense together

---

## 常见 Mistakes

- **Writing headlines that only work together** — RSA headlines get combined randomly
- **Ignoring character limits** — Platforms truncate without warning
- **All variations sound the same** — Vary angles, not just word choice
- **No CTA headlines** — RSAs need action-oriented headlines to drive 点击; include at least 2-3
- **Generic descriptions** — "Learn more about our solution" wastes the slot
- **Iterating without data** — Gut feelings are less reliable than 指标
- **测试 too many things at once** — Change one variable per test cycle
- **Retiring creative too early** — Allow 1,000+ 曝光 before judging

---

## Tool Integrations

For pulling 表现 data and managing 广告活动, see the [tools registry](../../tools/REGISTRY.md).

| 平台 | Pull 表现 Data | Manage 广告活动 | Guide |
|----------|:---------------------:|:----------------:|-------|
| **Google Ads** | `google-ads campaigns list`, `google-ads reports get` | `google-ads campaigns create` | [google-ads.md](../../tools/integrations/google-ads.md) |
| **Meta Ads** | `meta-ads insights get` | `meta-ads campaigns list` | [meta-ads.md](../../tools/integrations/meta-ads.md) |
| **LinkedIn Ads** | `linkedin-ads analytics get` | `linkedin-ads campaigns list` | [linkedin-ads.md](../../tools/integrations/linkedin-ads.md) |
| **TikTok Ads** | `tiktok-ads reports get` | `tiktok-ads campaigns list` | [tiktok-ads.md](../../tools/integrations/tiktok-ads.md) |

### 工作流: Pull Data, Analyze, Generate

```bash
# 1. Pull recent ad performance
node tools/clis/google-ads.js reports get --type ad_performance --date-range last_30_days

# 2. Analyze output (identify top/bottom performers)
# 3. Feed winning patterns into this skill
# 4. Generate new variations
# 5. Upload to platform
```

---

## Related Skills

- **paid-ads**: For 广告活动 strategy, targeting, budgets, and 优化
- **copywriting**: For 落地页 文案 (where ad traffic lands)
- **ab-test-配置方式**: For structuring creative tests with statistical rigor
- **营销-psychology**: For psychological principles behind high-performing creative
- **文案-editing**: For polishing ad 文案 before launch
