---
name: product-marketing-context
description: "当用户想创建或更新产品营销上下文文档时使用。用户提到“product context”“marketing context”“set up context”“positioning”“who is my target audience”“describe my product”“ICP”“ideal customer profile”或希望避免在不同营销任务里反复解释基础信息时也应使用。这个技能适合在新项目开始时优先运行，会生成 `.agents/product-marketing-context.md`，供其他营销技能复用产品、受众与定位信息。"
metadata:
  version: 1.1.0
---

# 产品 营销 背景

You help users create and maintain a 产品 营销 context document. This captures foundational positioning and messaging information that other 营销 skills 参考, so users don't repeat themselves.

The document is stored at `.agents/product-marketing-context.md`.

## 工作流

### 步骤 1: Check for Existing 背景

First, check if `.agents/product-marketing-context.md` already exists. Also check `.claude/product-marketing-context.md` for older setups — if found there but not in `.agents/`, offer to move it.

**If it exists:**
- Read it and summarize what's captured
- Ask which sections they want to update
- Only gather info for those sections

**If it doesn't exist, offer two options:**

1. **Auto-draft from codebase** (recommended): You'll study the repo—README, landing pages, 营销 文案, package.json, etc.—and draft a V1 of the context document. The user then reviews, corrects, and fills gaps. This is faster than starting from scratch.

2. **Start from scratch**: Walk through each section conversationally, gathering info one section at a time.

Most users prefer option 1. After presenting the draft, ask: "What needs correcting? What's missing?"

### 步骤 2: Gather Information

**If auto-drafting:**
1. Read the codebase: README, landing pages, 营销 文案, about pages, meta descriptions, package.json, any existing docs
2. Draft all sections based on what you find
3. Present the draft and ask what needs correcting or is missing
4. Iterate until the user is satisfied

**If starting from scratch:**
Walk through each section below conversationally, one at a time. Don't dump all questions at once.

For each section:
1. Briefly explain what you're capturing
2. Ask relevant questions
3. Confirm accuracy
4. Move to the next

Push for verbatim 客户 language — exact phrases are more valuable than polished descriptions because they reflect how 客户 actually think and speak, which makes 文案 more resonant.

---

## Sections to Capture

### 1. 产品 概览
- One-line description
- What it does (2-3 sentences)
- 产品 category (what "shelf" you sit on—how 客户 搜索 for you)
- 产品 类型 (SaaS, marketplace, e-commerce, service, etc.)
- Business model and pricing

### 2. Target 受众
- Target company 类型 (industry, size, stage)
- Target decision-makers (roles, departments)
- Primary use case (the main 问题 you solve)
- Jobs to be done (2-3 things 客户 "hire" you for)
- Specific use cases or scenarios

### 3. Personas (B2B only)
If multiple stakeholders are involved in buying, capture for each:
- User, Champion, Decision Maker, Financial Buyer, Technical Influencer
- What each cares about, their challenge, and the value you promise them

### 4. Problems & Pain Points
- Core challenge 客户 face before finding you
- Why current solutions fall short
- What it costs them (time, money, opportunities)
- Emotional tension (stress, fear, doubt)

### 5. Competitive Landscape
- **Direct competitors**: Same solution, same 问题 (e.g., Calendly vs SavvyCal)
- **Secondary competitors**: Different solution, same 问题 (e.g., Calendly vs Superhuman scheduling)
- **Indirect competitors**: Conflicting approach (e.g., Calendly vs personal assistant)
- How each falls short for 客户

### 6. Differentiation
- Key differentiators (能力 alternatives lack)
- How you solve it differently
- Why that's better (收益)
- Why 客户 choose you over alternatives

### 7. 异议 & Anti-Personas
- Top 3 异议 heard in sales and how to address them
- Who is NOT a good fit (anti-persona)

### 8. Switching Dynamics
The JTBD Four Forces:
- **Push**: What frustrations drive them away from current solution
- **Pull**: What attracts them to you
- **Habit**: What keeps them stuck with current approach
- **Anxiety**: What worries them about switching

### 9. 客户 Language
- How 客户 describe the 问题 (verbatim)
- How they describe your solution (verbatim)
- Words/phrases to use
- Words/phrases to avoid
- Glossary of 产品-specific terms

### 10. Brand Voice
- Tone (professional, casual, playful, etc.)
- Communication style (direct, conversational, technical)
- Brand personality (3-5 adjectives)

### 11. 证明材料
- Key 指标 or results to cite
- Notable 客户/logos
- Testimonial snippets
- Main value themes and supporting evidence

### 12. Goals
- Primary business goal
- Key conversion action (what you want people to do)
- Current 指标 (if known)

---

## 步骤 3: Create the Document

After gathering information, create `.agents/product-marketing-context.md` with this structure:

```markdown
# Product Marketing 背景

*Last updated: [date]*

## Product 概览
**One-liner:**
**What it does:**
**Product category:**
**Product type:**
**Business model:**

## Target Audience
**Target companies:**
**Decision-makers:**
**Primary use case:**
**Jobs to be done:**
-
**Use cases:**
-

## Personas
| Persona | Cares about | Challenge | Value we promise |
|---------|-------------|-----------|------------------|
| | | | |

## Problems & Pain Points
**Core problem:**
**Why alternatives fall short:**
-
**What it costs them:**
**Emotional tension:**

## Competitive Landscape
**Direct:** [Competitor] — falls short because...
**Secondary:** [Approach] — falls short because...
**Indirect:** [Alternative] — falls short because...

## Differentiation
**Key differentiators:**
-
**How we do it differently:**
**Why that's better:**
**Why customers choose us:**

## Objections
| Objection | Response |
|-----------|----------|
| | |

**Anti-persona:**

## Switching Dynamics
**Push:**
**Pull:**
**Habit:**
**Anxiety:**

## Customer Language
**How they describe the problem:**
- "[verbatim]"
**How they describe us:**
- "[verbatim]"
**Words to use:**
**Words to avoid:**
**Glossary:**
| Term | Meaning |
|------|---------|
| | |

## Brand Voice
**Tone:**
**Style:**
**Personality:**

## Proof Points
**Metrics:**
**Customers:**
**Testimonials:**
> "[quote]" — [who]
**Value themes:**
| Theme | Proof |
|-------|-------|
| | |

## Goals
**Business goal:**
**Conversion action:**
**Current metrics:**
```

---

## 步骤 4: Confirm and Save

- Show the completed document
- Ask if anything needs adjustment
- Save to `.agents/product-marketing-context.md`
- Tell them: "Other 营销 skills will now use this context automatically. Run `/product-marketing-context` anytime to update it."

---

## Tips

- **Be specific**: Ask "What's the #1 frustration that brings them to you?" not "What 问题 do they solve?"
- **Capture exact words**: 客户 language beats polished descriptions
- **Ask for examples**: "Can you give me an 示例?" unlocks better answers
- **Validate as you go**: Summarize each section and confirm before moving on
- **Skip what doesn't apply**: Not every 产品 needs all sections (e.g., Personas for B2C)
