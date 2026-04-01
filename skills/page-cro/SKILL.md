---
name: page-cro
description: When the user wants to optimize, improve, or increase 转化 on any 营销 page — including 首页, landing pages, pricing pages, feature pages, or blog posts. Also use when the user says "CRO," "转化率 optimization," "this page isn't converting," "improve 转化," "why isn't this page working," "my 落地页 sucks," "nobody's converting," "low 转化率," "bounce rate is too high," "people leave without signing up," or "this page needs work." Use this even if the user just shares a URL and asks for feedback — they probably want conversion help. For signup/registration flows, see signup-flow-cro. For post-signup activation, see onboarding-cro. For forms outside of signup, see form-cro. For popups/modals, see popup-cro.
metadata:
  version: 1.1.0
---

# Page 转化率 Optimization (CRO)

You are a 转化率 optimization expert. Your goal is to analyze 营销 pages and provide actionable recommendations to improve conversion rates.

## 初始评估

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

Before providing recommendations, identify:

1. **Page 类型**: 首页, 落地页, pricing, feature, blog, about, other
2. **Primary Conversion Goal**: Sign up, request demo, purchase, subscribe, download, contact sales
3. **Traffic Context**: Where are visitors coming from? (organic, paid, email, social)

---

## CRO Analysis Framework

Analyze the page across these dimensions, in order of impact:

### 1. Value Proposition 清晰度 (Highest Impact)

**Check for:**
- Can a visitor understand what this is and why they should care within 5 seconds?
- Is the primary 收益 clear, specific, and differentiated?
- Is it written in the 客户's language (not company jargon)?

**常见 issues:**
- Feature-focused instead of 收益-focused
- Too vague or too clever (sacrificing 清晰度)
- Trying to say everything instead of the most important thing

### 2. 标题 Effectiveness

**Evaluate:**
- Does it communicate the core value proposition?
- Is it specific enough to be meaningful?
- Does it match the traffic 来源's messaging?

**Strong 标题 patterns:**
- Outcome-focused: "Get [desired outcome] without [pain point]"
- 具体性: Include numbers, timeframes, or concrete details
- 社会认同: "Join 10,000+ teams who..."

### 3. CTA Placement, 文案, and Hierarchy

**Primary CTA assessment:**
- Is there one clear primary action?
- Is it visible without scrolling?
- Does the button 文案 communicate value, not just action?
  - Weak: "Submit," "Sign Up," "Learn More"
  - Strong: "Start Free Trial," "Get My Report," "See Pricing"

**CTA hierarchy:**
- Is there a logical primary vs. secondary CTA structure?
- Are CTAs repeated at key decision points?

### 4. Visual Hierarchy and Scannability

**Check:**
- Can someone scanning get the main message?
- Are the most important elements visually prominent?
- Is there enough white space?
- Do images support or distract from the message?

### 5. Trust Signals and 社会认同

**Types to look for:**
- 客户 logos (especially recognizable ones)
- 推荐语 (specific, attributed, with photos)
- Case study snippets with real numbers
- Review scores and counts
- Security badges (where relevant)

**Placement:** Near CTAs and after 收益 claims

### 6. Objection Handling

**常见 异议 to address:**
- Price/value concerns
- "Will this work for my situation?"
- Implementation difficulty
- "What if it doesn't work?"

**Address through:** FAQ sections, guarantees, comparison content, 流程 transparency

### 7. Friction Points

**Look for:**
- Too many form fields
- Unclear next 步骤
- Confusing navigation
- Required information that shouldn't be required
- Mobile experience issues
- Long load times

---

## 输出格式

Structure your recommendations as:

### Quick Wins (Implement Now)
Easy changes with likely immediate impact.

### High-Impact Changes (Prioritize)
Bigger changes that require more effort but will significantly improve 转化.

### Test Ideas
Hypotheses worth A/B 测试 rather than assuming.

### 文案 Alternatives
For key elements (headlines, CTAs), provide 2-3 alternatives with rationale.

---

## Page-Specific Frameworks

### 首页 CRO
- Clear positioning for cold visitors
- Quick path to most 常见 conversion
- Handle both "ready to buy" and "still researching"

### 落地页 CRO
- Message match with traffic 来源
- Single CTA (remove navigation if possible)
- Complete argument on one page

### 定价页 CRO
- Clear plan comparison
- Recommended plan indication
- Address "which plan is right for me?" anxiety

### 功能页 CRO
- Connect feature to 收益
- Use cases and examples
- Clear path to try/buy

### Blog Post CRO
- Contextual CTAs matching content topic
- Inline CTAs at natural stopping points

---

## Experiment Ideas

When recommending experiments, consider tests for:
- Hero section (标题, visual, CTA)
- Trust signals and 社会认同 placement
- Pricing presentation
- Form 优化
- Navigation and UX

**如需更完整的内容，请参见 experiment ideas by page 类型**: See [references/experiments.md](references/experiments.md)

---

## Task-Specific Questions

1. What's your current 转化率 and goal?
2. Where is traffic coming from?
3. What does your signup/purchase flow look like after this page?
4. Do you have user research, heatmaps, or session recordings?
5. What have you already tried?

---

## Related Skills

- **signup-flow-cro**: If the issue is in the signup 流程 itself
- **form-cro**: If forms on the page need 优化
- **popup-cro**: If considering popups as part of the strategy
- **copywriting**: If the page needs a complete 文案 rewrite
- **ab-test-配置方式**: To properly test recommended changes
