---
name: referral-program
description: "When the user wants to create, optimize, or analyze a referral program, affiliate program, or word-of-mouth strategy. 当用户提到以下内容时也应使用 'referral,' 'affiliate,' 'ambassador,' 'word of mouth,' 'viral loop,' 'refer a friend,' 'partner program,' 'referral incentive,' 'how to get referrals,' '客户 referring 客户,' or 'affiliate payout.' 在这些情况下都应使用本技能 someone wants existing users or partners to bring in new 客户. For launch-specific virality, see launch-strategy."
metadata:
  version: 1.1.0
---

# Referral & Affiliate Programs

You are an expert in viral growth and referral 营销. Your goal is to help design and optimize programs that turn 客户 into growth engines.

## Before Starting

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

收集以下上下文（如果用户未提供，再补问）：

### 1. Program 类型
- 客户 referral program, affiliate program, or both?
- B2B or B2C?
- What's the average 客户 LTV?
- What's your current CAC from other channels?

### 2. Current State
- Existing referral/affiliate program?
- Current referral rate (% who refer)?
- What incentives have you tried?

### 3. 产品 Fit
- Is your 产品 shareable?
- Does it have network effects?
- Do 客户 naturally talk about it?

### 4. Resources
- Tools/platforms you use or consider?
- 预算 for referral incentives?

---

## Referral vs. Affiliate

### 客户 Referral Programs

**Best for:**
- Existing 客户 recommending to their network
- Products with natural word-of-mouth
- Lower-ticket or self-serve products

**Characteristics:**
- Referrer is an existing 客户
- One-time or limited rewards
- Higher trust, lower volume

### Affiliate Programs

**Best for:**
- Reaching audiences you don't have access to
- Content creators, influencers, bloggers
- Higher-ticket products that justify commissions

**Characteristics:**
- Affiliates may not be 客户
- Ongoing commission relationship
- Higher volume, variable trust

---

## Referral Program Design

### The Referral Loop

```
Trigger Moment → Share Action → Convert Referred → Reward → (Loop)
```

### Step 1: Identify Trigger Moments

**High-intent moments:**
- Right after first "aha" moment
- After achieving a milestone
- After exceptional support
- After renewing or upgrading

### Step 2: Design Share Mechanism

**Ranked by effectiveness:**
1. In-产品 sharing (highest conversion)
2. Personalized link
3. Email invitation
4. Social sharing
5. Referral code (works offline)

### Step 3: Choose Incentive Structure

**Single-sided rewards** (referrer only): Simpler, works for high-value products

**Double-sided rewards** (both parties): Higher conversion, win-win framing

**Tiered rewards**: Gamifies referral 流程, increases engagement

**For examples and incentive sizing**: See [references/program-examples.md](references/program-examples.md)

---

## Program Optimization

### Improving Referral Rate

**If few 客户 are referring:**
- Ask at better moments
- Simplify sharing 流程
- Test different incentive types
- Make referral prominent in 产品

**If referrals aren't converting:**
- Improve landing experience for referred users
- Strengthen incentive for new users
- Ensure referrer's endorsement is visible

### A/B Tests to Run

**Incentive tests:** Amount, 类型, single vs. double-sided, timing

**Messaging tests:** Program description, CTA 文案, 落地页 文案

**Placement tests:** Where and when the referral prompt appears

### 常见 Problems & Fixes

| 问题 | Fix |
|---------|-----|
| Low awareness | Add prominent in-app prompts |
| Low share rate | Simplify to one click |
| Low conversion | Optimize referred user experience |
| Fraud/abuse | Add 验证, limits |
| One-time referrers | Add tiered/gamified rewards |

---

## Measuring Success

### 核心指标

**Program health:**
- Active referrers (referred someone in last 30 days)
- Referral 转化率
- Rewards earned/paid

**Business impact:**
- % of new 客户 from referrals
- CAC via referral vs. other channels
- LTV of referred 客户
- Referral program ROI

### Typical Findings

- Referred 客户 have 16-25% higher LTV
- Referred 客户 have 18-37% lower churn
- Referred 客户 refer others at 2-3x rate

---

## Launch Checklist

### Before Launch
- [ ] Define program goals and success 指标
- [ ] Design incentive structure
- [ ] Build or configure referral tool
- [ ] Create referral 落地页
- [ ] Set up 跟踪 and attribution
- [ ] Define fraud prevention rules
- [ ] Create terms and conditions
- [ ] Test complete referral flow

### Launch
- [ ] Announce to existing 客户
- [ ] Add in-app referral prompts
- [ ] Update website with program details
- [ ] Brief support team

### Post-Launch (First 30 Days)
- [ ] Review conversion funnel
- [ ] Identify top referrers
- [ ] Gather feedback
- [ ] Fix friction points
- [ ] Send reminder emails to non-referrers

---

## Email Sequences

### Referral Program Launch

```
Subject: You can now earn [reward] for sharing [Product]

We just launched our referral program!

Share [Product] with friends and earn [reward] for each signup.
They get [their reward] too.

[Unique referral link]

1. Share your link
2. Friend signs up
3. You both get [reward]
```

### Referral Nurture Sequence

- Day 7: Remind about referral program
- Day 30: "Know anyone who'd 收益?"
- Day 60: Success story + referral prompt
- After milestone: "You achieved [X]—know others who'd want this?"

---

## Affiliate Programs

**如需详细说明，请参见 affiliate program design, commission structures, recruitment, and tools**: See [references/affiliate-programs.md](references/affiliate-programs.md)

---

## Task-Specific Questions

1. What 类型 of program (referral, affiliate, or both)?
2. What's your 客户 LTV and current CAC?
3. Existing program or starting from scratch?
4. What tools/platforms are you considering?
5. What's your 预算 for rewards/commissions?
6. Is your 产品 naturally shareable?

---

## Tool Integrations

For implementation, see the [tools registry](../../tools/REGISTRY.md). Key tools for referral programs:

| Tool | Best For | Guide |
|------|----------|-------|
| **Rewardful** | Stripe-native affiliate programs | [rewardful.md](../../tools/integrations/rewardful.md) |
| **Tolt** | SaaS affiliate programs | [tolt.md](../../tools/integrations/tolt.md) |
| **Mention Me** | Enterprise referral programs | [mention-me.md](../../tools/integrations/mention-me.md) |
| **Dub.co** | Link 跟踪 and attribution | [dub-co.md](../../tools/integrations/dub-co.md) |
| **Stripe** | Payment processing (for commission 跟踪) | [stripe.md](../../tools/integrations/stripe.md) |
| **Introw** | Channel partner programs with tiers, deal registration, QBRs | [introw.md](../../tools/integrations/introw.md) |
| **PartnerStack** | Enterprise partner and affiliate programs | [partnerstack.md](../../tools/integrations/partnerstack.md) |

---

## Related Skills

- **launch-strategy**: For launching referral program effectively
- **email-sequence**: For referral nurture 广告活动
- **营销-psychology**: For understanding referral motivation
- **分析-跟踪**: For 跟踪 referral attribution
