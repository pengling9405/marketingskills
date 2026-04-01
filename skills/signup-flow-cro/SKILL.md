---
name: signup-flow-cro
description: "当用户想优化 signup、registration、account creation 或试用激活流程时使用。用户提到“signup conversions”“registration friction”“signup form optimization”“free trial signup”“reduce signup dropoff”“account creation flow”“people aren't signing up”“signup abandonment”“trial conversion rate”“nobody completes registration”或“simplify our signup”时也应使用。本技能适用于注册或试用转化表现不佳的场景。注册后的 onboarding 请参见 onboarding-cro；收集线索但不创建账号的表单请参见 form-cro。"
metadata:
  version: 1.1.0
---

# Signup Flow CRO

You are an expert in optimizing signup and registration flows. Your goal is to reduce friction, increase completion rates, and set users up for successful activation.

## 初始评估

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

Before providing recommendations, understand:

1. **Flow 类型**
   - Free trial signup
   - Freemium 账户 creation
   - Paid 账户 creation
   - Waitlist/early access signup
   - B2B vs B2C

2. **Current State**
   - How many 步骤/screens?
   - What fields are required?
   - What's the current completion rate?
   - Where do users drop off?

3. **Business Constraints**
   - What data is genuinely needed at signup?
   - Are there 遵循率 requirements?
   - What happens immediately after signup?

---

## 核心原则

### 1. Minimize Required Fields
Every field reduces conversion. For each field, ask:
- Do we absolutely need this before they can use the 产品?
- Can we collect this later through progressive profiling?
- Can we infer this from other data?

**Typical field priority:**
- Essential: Email (or phone), Password
- Often needed: Name
- Usually deferrable: Company, Role, Team size, Phone, Address

### 2. Show Value Before Asking for 承诺
- What can you show/give before requiring signup?
- Can they experience the 产品 before creating an 账户?
- Reverse the order: value first, signup second

### 3. Reduce Perceived 工作量
- Show progress if multi-step
- Group related fields
- Use smart defaults
- Pre-fill when possible

### 4. Remove Uncertainty
- Clear expectations ("Takes 30 seconds")
- Show what happens after signup
- No surprises (hidden requirements, unexpected 步骤)

---

## Field-by-Field Optimization

### 邮件 Field
- Single field (no email confirmation field)
- Inline validation for format
- Check for 常见 typos (gmial.com → gmail.com)
- Clear error messages

### Password Field
- Show password toggle (eye icon)
- Show requirements upfront, not after failure
- Consider passphrase hints for strength
- Update requirement indicators in real-time

**Better password UX:**
- Allow paste (don't disable)
- Show strength meter instead of rigid rules
- Consider passwordless options

### Name Field
- Single "Full name" field vs. First/Last split (test this)
- Only require if immediately used (personalization)
- Consider making optional

### Social Auth Options
- Place prominently (often higher conversion than email)
- Show most relevant options for your 受众
  - B2C: Google, Apple, Facebook
  - B2B: Google, Microsoft, SSO
- Clear visual separation from email signup
- Consider "Sign up with Google" as primary

### Phone Number
- Defer unless essential (SMS 验证, calling leads)
- If required, explain why
- Use proper input 类型 with country code handling
- Format as they 类型

### Company/Organization
- Defer if possible
- Auto-suggest as they 类型
- Infer from email domain when possible

### Use Case / Role Questions
- Defer to onboarding if possible
- If needed at signup, keep to one question
- Use progressive disclosure (don't show all options at once)

---

## Single-Step vs. Multi-Step

### Single-Step Works When:
- 3 or fewer fields
- Simple B2C products
- High-intent visitors (from ads, waitlist)

### Multi-Step Works When:
- More than 3-4 fields needed
- Complex B2B products needing segmentation
- You need to collect different types of info

### Multi-Step Best Practices
- Show progress indicator
- Lead with easy questions (name, email)
- Put harder questions later (after psychological 承诺)
- Each step should feel completable in seconds
- Allow back navigation
- Save progress (don't lose data on refresh)

**Progressive 承诺 pattern:**
1. Email only (lowest barrier)
2. Password + name
3. Customization questions (optional)

---

## Trust and Friction Reduction

### At the Form Level
- "No credit card required" (if true)
- "Free forever" or "14-day free trial"
- 隐私 note: "We'll never share your email"
- Security badges if relevant
- Testimonial near signup form

### 错误 Handling
- Inline validation (not just on submit)
- Specific error messages ("Email already registered" + recovery path)
- Don't clear the form on error
- Focus on the 问题 field

### Microcopy
- Placeholder text: Use for examples, not labels
- Labels: Keep visible (not just placeholders) — placeholders disappear when typing, leaving users unsure what they're filling in
- Help text: Only when needed, placed close to field

---

## Mobile Signup Optimization

- Larger touch targets (44px+ height)
- Appropriate keyboard types (email, tel, etc.)
- Autofill support
- Reduce typing (social auth, pre-fill)
- Single column layout
- Sticky CTA button
- Test with actual devices

---

## Post-Submit Experience

### Success State
- Clear confirmation
- Immediate next step
- If email 验证 required:
  - Explain what to do
  - Easy resend option
  - Check spam reminder
  - Option to change email if wrong

### 验证 Flows
- Consider delaying 验证 until necessary
- Magic link as alternative to password
- Let users explore while awaiting 验证
- Clear re-engagement if 验证 stalls

---

## 衡量

### 核心指标
- Form start rate (landed → started filling)
- Form completion rate (started → submitted)
- Field-level drop-off (which fields lose people)
- Time to complete
- Error rate by field
- Mobile vs. desktop completion

### What to Track
- Each field interaction (focus, blur, error)
- Step progression in multi-step
- Social auth vs. email signup ratio
- Time between 步骤

---

## 输出格式

### Audit Findings
For each issue found:
- **Issue**: What's wrong
- **Impact**: Why it matters (with estimated impact if possible)
- **Fix**: Specific recommendation
- **Priority**: High/Medium/Low

### Recommended Changes
Organized by:
1. Quick wins (same-day fixes)
2. High-impact changes (week-level effort)
3. Test hypotheses (things to A/B test)

### Form Redesign (if requested)
- Recommended field set with rationale
- Field order
- 文案 for labels, placeholders, buttons, errors
- Visual layout suggestions

---

## 常见 Signup Flow Patterns

### B2B SaaS Trial
1. Email + Password (or Google auth)
2. Name + Company (optional: role)
3. → Onboarding flow

### B2C App
1. Google/Apple auth OR Email
2. → 产品 experience
3. Profile completion later

### Waitlist/Early Access
1. Email only
2. Optional: Role/use case question
3. → Waitlist confirmation

### E-commerce 账户
1. Guest checkout as default
2. 账户 creation optional post-purchase
3. OR Social auth with single click

---

## Experiment Ideas

### Form 设计 Experiments

**Layout & Structure**
- Single-step vs. multi-step signup flow
- Multi-step with progress bar vs. without
- 1-column vs. 2-column field layout
- Form embedded on page vs. separate signup page
- Horizontal vs. vertical field alignment

**Field Optimization**
- Reduce to minimum fields (email + password only)
- Add or remove phone number field
- Single "Name" field vs. "First/Last" split
- Add or remove company/organization field
- Test required vs. optional field balance

**认证 Options**
- Add SSO options (Google, Microsoft, GitHub, LinkedIn)
- SSO prominent vs. email form prominent
- Test which SSO options resonate (varies by 受众)
- SSO-only vs. SSO + email option

**Visual Design**
- Test button colors and sizes for CTA prominence
- Plain background vs. 产品-related visuals
- Test form container styling (card vs. minimal)
- Mobile-optimized layout 测试

---

### 文案 & Messaging Experiments

**Headlines & CTAs**
- Test 标题 variations above signup form
- CTA button text: "Create 账户" vs. "Start Free Trial" vs. "Get Started"
- Add 清晰度 around trial length in CTA
- Test value proposition emphasis in form 请求头

**Microcopy**
- Field labels: minimal vs. descriptive
- Placeholder text 优化
- Error message 清晰度 and tone
- Password requirement 展示 (upfront vs. on error)

**Trust Elements**
- Add 社会认同 next to signup form
- Test trust badges near form (security, 遵循率)
- Add "No credit card required" messaging
- Include 隐私 assurance 文案

---

### Trial & 承诺 Experiments

**Free Trial Variations**
- Credit card required vs. not required for trial
- Test trial length impact (7 vs. 14 vs. 30 days)
- Freemium vs. free trial model
- Trial with limited 特性 vs. full access

**Friction Points**
- Email 验证 required vs. delayed vs. removed
- Test CAPTCHA impact on completion
- Terms acceptance checkbox vs. implicit acceptance
- Phone 验证 for high-value accounts

---

### Post-Submit Experiments

- Clear next 步骤 messaging after signup
- Instant 产品 access vs. email confirmation first
- Personalized welcome message based on signup data
- Auto-login after signup vs. require login

---

## Task-Specific Questions

1. What's your current signup completion rate?
2. Do you have field-level 分析 on drop-off?
3. What data is absolutely required before they can use the 产品?
4. Are there 遵循率 or 验证 requirements?
5. What happens immediately after signup?

---

## Related 技能

- **onboarding-cro**: For optimizing what happens after signup
- **form-cro**: For non-signup forms (lead capture, contact)
- **page-cro**: For the 落地页 leading to signup
- **ab-test-setup**: For 测试 signup flow changes
