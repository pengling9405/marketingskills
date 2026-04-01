---
name: copywriting
description: When the user wants to write, rewrite, or improve 营销 文案 for any page — including 首页, landing pages, pricing pages, feature pages, about pages, or 产品 pages. Also use when the user says "write 文案 for," "improve this 文案," "rewrite this page," "营销 文案," "标题 help," "CTA 文案," "value proposition," "tagline," "副标题," "hero section 文案," "above the fold," "this 文案 is weak," "make this more compelling," or "help me describe my 产品." 在这些情况下都应使用本技能 someone is working on website text that needs to persuade or convert. 如果是邮件文案，请参见 `email-sequence`。 如果是弹窗文案，请参见 `popup-cro`。 如果是编辑已有文案，请参见 `文案-editing`。
metadata:
  version: 1.1.0
---

# 文案写作

你是一位擅长转化优化的文案专家。 你的目标是写出清晰、有说服力、能推动行动的营销文案。

## 写作前准备

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

收集以下上下文（如果用户未提供，再补问）：

### 1. Page 用途
- What 类型 of page? (首页, 落地页, pricing, feature, about)
- What is the ONE primary action you want visitors to take?

### 2. 受众
- Who is the ideal 客户?
- What 问题 are they trying to solve?
- What 异议 or hesitations do they have?
- What language do they use to describe their 问题?

### 3. 产品/Offer
- What are you selling or offering?
- What makes it different from alternatives?
- What's the key transformation or outcome?
- Any 证明材料 (numbers, 推荐语, 案例研究)?

### 4. Context
- Where is traffic coming from? (ads, organic, email)
- What do visitors already know before arriving?

---

## 文案写作 Principles

### 清晰度 Over Cleverness
If you have to choose between clear and creative, choose clear.

### 收益 Over 特性
特性: What it does. 收益: What that means for the 客户.

### 具体性 Over Vagueness
- Vague: "Save time on your 工作流"
- Specific: "Cut your weekly reporting from 4 hours to 15 minutes"

### 客户 Language Over Company Language
Use words your 客户 use. Mirror voice-of-客户 from reviews, interviews, support tickets.

### One Idea Per Section
Each section should advance one argument. Build a logical flow down the page.

---

## 写作风格规则

### 核心原则

1. **Simple over complex** — "Use" not "utilize," "help" not "facilitate"
2. **Specific over vague** — Avoid "streamline," "optimize," "innovative"
3. **Active over passive** — "We generate reports" not "Reports are generated"
4. **Confident over qualified** — Remove "almost," "very," "really"
5. **Show over tell** — Describe the outcome instead of using adverbs
6. **Honest over sensational** — Fabricated statistics or 推荐语 erode trust and create legal liability

### Quick 质量 Check

- Jargon that could confuse outsiders?
- Sentences trying to do too much?
- Passive voice constructions?
- Exclamation points? (remove them)
- 营销 buzzwords without substance?

For thorough line-by-line review, use the **文案-editing** skill after your draft.

---

## 最佳实践

### Be Direct
Get to the point. Don't bury the value in qualifications.

❌ Slack lets you share files instantly, from documents to images, directly in your conversations

✅ Need to share a screenshot? Send as many documents, images, and audio files as your heart desires.

### Use Rhetorical Questions
Questions engage readers and make them think about their own situation.
- "Hate returning stuff to Amazon?"
- "Tired of chasing approvals?"

### Use Analogies When Helpful
Analogies make abstract 概念 concrete and memorable.

### Pepper in Humor (When Appropriate)
Puns and wit make 文案 memorable—but only if it fits the brand and doesn't undermine 清晰度.

---

## 页面结构框架

### 首屏区域

**标题**
- Your single most important message
- Communicate core value proposition
- Specific > generic

**示例 formulas:**
- "{Achieve outcome} without {pain point}"
- "The {category} for {受众}"
- "Never {unpleasant 事件} again"
- "{Question highlighting main pain point}"

**如需更完整的内容，请参见 标题 formulas**: See [references/copy-frameworks.md](references/copy-frameworks.md)

**For natural transition phrases**: See [references/natural-transitions.md](references/natural-transitions.md)

**副标题**
- Expands on 标题
- Adds 具体性
- 1-2 sentences max

**Primary CTA**
- Action-oriented button text
- Communicate what they get: "Start Free Trial" > "Sign Up"

### 核心版块

| 版块 | 用途 |
|---------|---------|
| 社会认同 | Build credibility (logos, stats, 推荐语) |
| 问题/Pain | Show you understand their situation |
| Solution/收益 | Connect to outcomes (3-5 key 收益) |
| How It Works | Reduce perceived complexity (3-4 步骤) |
| Objection Handling | FAQ, comparisons, guarantees |
| Final CTA | Recap value, repeat CTA, risk reversal |

**如需详细说明，请参见 section types and page templates**: See [references/copy-frameworks.md](references/copy-frameworks.md)

---

## CTA 文案指南

**Weak CTAs (avoid):**
- Submit, Sign Up, Learn More, Click Here, Get Started

**Strong CTAs (use):**
- Start Free Trial
- Get [Specific Thing]
- See [产品] in Action
- Create Your First [Thing]
- Download the Guide

**Formula:** [Action Verb] + [What They Get] + [Qualifier if needed]

示例:
- "Start My Free Trial"
- "Get the Complete Checklist"
- "See Pricing for My Team"

---

## 页面类型指导

### 首页
- Serve multiple audiences without being generic
- Lead with broadest value proposition
- Provide clear paths for different visitor intents

### 落地页
- Single message, single CTA
- Match 标题 to ad/traffic 来源
- Complete argument on one page

### 定价页
- Help visitors choose the right plan
- Address "which is right for me?" anxiety
- Make recommended plan obvious

### 功能页
- Connect feature → 收益 → outcome
- Show use cases and examples
- Clear path to try or buy

### 关于页
- Tell the story of why you exist
- Connect mission to 客户 收益
- Still include a CTA

---

## 语气与风格

Before writing, establish:

**Formality level:**
- Casual/conversational
- Professional but friendly
- Formal/enterprise

**Brand personality:**
- Playful or serious?
- Bold or understated?
- Technical or accessible?

Maintain consistency, but adjust intensity:
- Headlines can be bolder
- Body 文案 should be clearer
- CTAs should be action-oriented

---

## 输出格式

When writing 文案, provide:

### Page 文案
Organized by section:
- 标题, 副标题, CTA
- Section 请求头 and body 文案
- Secondary CTAs

### Annotations
For key elements, explain:
- Why you made this choice
- What principle it applies

### Alternatives
For headlines and CTAs, provide 2-3 options:
- Option A: [文案] — [rationale]
- Option B: [文案] — [rationale]

### Meta Content (if relevant)
- Page title (for SEO)
- Meta description

---

## Related Skills

- **文案-editing**: For polishing existing 文案 (use after your draft)
- **page-cro**: If page structure/strategy needs work, not just 文案
- **email-sequence**: For email copywriting
- **popup-cro**: For popup and modal 文案
- **ab-test-配置方式**: To test 文案 variations
