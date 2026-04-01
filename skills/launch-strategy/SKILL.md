---
name: launch-strategy
description: "当用户想规划产品发布、功能公告或 release strategy 时使用。用户提到“launch”“Product Hunt”“feature release”“announcement”“go-to-market”“beta launch”“early access”“waitlist”“product update”“launch checklist”“GTM plan”或“we're about to ship”时也应使用。本技能适用于任何即将对外发布产品、功能或更新的场景。发布后的持续营销请参见 marketing-ideas。"
metadata:
  version: 1.1.0
---

# Launch 策略

You are an expert in SaaS 产品 launches and feature announcements. Your goal is to help users plan launches that build momentum, capture attention, and convert interest into users.

## Before Starting

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

---

## Core Philosophy

The best companies don't just launch once—they launch again and again. Every new feature, improvement, and update is an opportunity to capture attention and engage your 受众.

A strong launch isn't about a single moment. It's about:
- Getting your 产品 into users' hands early
- Learning from real feedback
- Making a splash at every stage
- Building momentum that compounds over time

---

## The ORB Framework

Structure your launch 营销 across three channel types. Everything should ultimately lead back to owned channels.

### Owned Channels
You own the channel (though not the 受众). Direct access without algorithms or 平台 rules.

**示例:**
- Email list
- Blog
- Podcast
- Branded community (Slack, Discord)
- Website/产品

**Why they matter:**
- Get more effective over time
- No algorithm changes or pay-to-play
- Direct relationship with 受众
- Compound value from content

**Start with 1-2 based on 受众:**
- Industry lacks 质量 content → Start a blog
- People want direct updates → Focus on email
- Engagement matters → Build a community

**示例 - Superhuman:**
Built demand through an invite-only waitlist and one-on-one onboarding sessions. Every new user got a 30-minute live demo. This created exclusivity, FOMO, and word-of-mouth—all through owned relationships. Years later, their original onboarding materials still drive engagement.

### Rented Channels
Platforms that provide visibility but you don't control. Algorithms shift, rules change, pay-to-play increases.

**示例:**
- Social media (Twitter/X, LinkedIn, Instagram)
- App stores and marketplaces
- YouTube
- Reddit

**How to use correctly:**
- Pick 1-2 platforms where your 受众 is active
- Use them to drive traffic to owned channels
- Don't rely on them as your only strategy

**示例 - Notion:**
Hacked virality through Twitter, YouTube, and Reddit where productivity enthusiasts were active. Encouraged community to share templates and 工作流. But they funneled all visibility into owned assets—every viral post led to signups, then targeted email onboarding.

**平台-specific tactics:**
- Twitter/X: Threads that spark conversation → link to newsletter
- LinkedIn: High-value posts → lead to gated content or email signup
- Marketplaces (Shopify, Slack): Optimize listing → drive to site for more

Rented channels give speed, not stability. Capture momentum by bringing users into your owned ecosystem.

### Borrowed Channels
Tap into someone else's 受众 to shortcut the hardest part—getting noticed.

**示例:**
- Guest content (blog posts, podcast interviews, newsletter 特性)
- Collaborations (webinars, co-营销, social takeovers)
- Speaking engagements (conferences, panels, virtual summits)
- Influencer partnerships

**Be proactive, not passive:**
1. List industry leaders your 受众 follows
2. Pitch win-win collaborations
3. Use tools like SparkToro or Listen 说明 to find 受众 overlap
4. Set up affiliate/referral incentives (for channel partner launches, use [Introw](../../tools/integrations/introw.md) to manage deal registration and commissions)

**示例 - TRMNL:**
Sent a free e-ink 展示 to YouTuber Snazzy Labs—not a paid sponsorship, just hoping he'd like it. He created an in-depth review that racked up 500K+ views and drove $500K+ in sales. They also set up an affiliate program for ongoing promotion.

Borrowed channels give instant credibility, but only work if you convert borrowed attention into owned relationships.

---

## Five-Phase Launch Approach

Launching isn't a one-day 事件. It's a phased 流程 that builds momentum.

### 阶段 1: Internal Launch
Gather initial feedback and iron out major issues before going public.

**Actions:**
- Recruit early users one-on-one to test for free
- Collect feedback on usability gaps and missing 特性
- Ensure prototype is functional enough to demo (doesn't need to be production-ready)

**Goal:** Validate core functionality with friendly users.

### 阶段 2: Alpha Launch
Put the 产品 in front of external users in a controlled way.

**Actions:**
- Create 落地页 with early access signup form
- Announce the 产品 exists
- Invite users individually to start 测试
- MVP should be working in production (even if still evolving)

**Goal:** First external validation and initial waitlist building.

### 阶段 3: Beta Launch
Scale up early access while generating external buzz.

**Actions:**
- Work through early access list (some free, some paid)
- Start 营销 with teasers about problems you solve
- Recruit friends, investors, and influencers to test and share

**Consider adding:**
- Coming soon 落地页 or waitlist
- "Beta" sticker in dashboard navigation
- Email invites to early access list
- Early access toggle in settings for experimental 特性

**Goal:** Build buzz and refine 产品 with broader feedback.

### 阶段 4: Early Access Launch
Shift from small-scale 测试 to controlled expansion.

**Actions:**
- Leak 产品 details: screenshots, feature GIFs, demos
- Gather quantitative usage data and qualitative feedback
- Run user research with engaged users (incentivize with credits)
- Optionally run 产品/market fit survey to refine messaging

**Expansion options:**
- Option A: Throttle invites in batches (5-10% at a time)
- Option B: Invite all users at once under "early access" framing

**Goal:** Validate at scale and prepare for full launch.

### Phase 5: Full Launch
Open the floodgates.

**Actions:**
- Open self-serve signups
- Start charging (if not already)
- Announce general availability across all channels

**Launch touchpoints:**
- 客户 emails
- In-app popups and 产品 tours
- Website banner linking to launch assets
- "New" sticker in dashboard navigation
- Blog post announcement
- Social posts across platforms
- 产品 Hunt, BetaList, Hacker News, etc.

**Goal:** Maximum visibility and conversion to paying users.

---

## 产品 Hunt Launch 策略

产品 Hunt can be powerful for reaching early adopters, but it's not magic—it requires preparation.

### Pros
- Exposure to tech-savvy early adopter 受众
- Credibility bump (especially if 产品 of the Day)
- Potential PR coverage and backlinks

### Cons
- Very competitive to rank well
- Short-lived traffic spikes
- Requires significant pre-launch planning

### How to Launch Successfully

**Before launch day:**
1. Build relationships with influential supporters, content hubs, and communities
2. Optimize your listing: compelling tagline, polished visuals, short demo 视频
3. Study successful launches to identify what worked
4. Engage in relevant communities—provide value before pitching
5. Prepare your team for all-day engagement

**On launch day:**
1. Treat it as an all-day 事件
2. Respond to every comment in real-time
3. Answer questions and spark discussions
4. Encourage your existing 受众 to engage
5. Direct traffic back to your site to capture signups

**After launch day:**
1. Follow up with everyone who engaged
2. Convert 产品 Hunt traffic into owned relationships (email signups)
3. Continue momentum with post-launch content

### 案例研究

**SavvyCal** (Scheduling tool):
- Optimized 落地页 and onboarding before launch
- Built relationships with productivity/SaaS influencers in advance
- Responded to every comment on launch day
- Result: #2 产品 of the Month

**Reform** (Form builder):
- Studied successful launches and applied insights
- Crafted clear tagline, polished visuals, demo 视频
- Engaged in communities before launch (provided value first)
- Treated launch as all-day engagement 事件
- Directed traffic to capture signups
- Result: #1 产品 of the Day

---

## Post-Launch 产品 营销

Your launch isn't over when the announcement goes live. Now comes adoption and retention work.

### Immediate Post-Launch Actions

**Educate new users:**
Set up automated onboarding 邮件序列 introducing key 特性 and use cases.

**Reinforce the launch:**
Include announcement in your weekly/biweekly/monthly roundup email to catch people who missed it.

**Differentiate against competitors:**
Publish comparison pages highlighting why you're the obvious choice.

**Update web pages:**
Add dedicated sections about the new feature/产品 across your site.

**Offer hands-on preview:**
Create no-code interactive demo (using tools like Navattic) so visitors can explore before signing up.

### Keep Momentum Going
It's easier to build on existing momentum than start from scratch. Every touchpoint reinforces the launch.

---

## Ongoing Launch 策略

Don't rely on a single launch 事件. Regular updates and feature rollouts sustain engagement.

### How to Prioritize What to Announce

Use this matrix to decide how much 营销 each update deserves:

**Major updates** (new 特性, 产品 overhauls):
- Full 广告活动 across multiple channels
- Blog post, email 广告活动, in-app messages, social media
- Maximize exposure

**Medium updates** (new integrations, UI enhancements):
- Targeted announcement
- Email to relevant segments, in-app banner
- Don't need full fanfare

**Minor updates** (bug fixes, small tweaks):
- Changelog and release notes
- Signal that 产品 is improving
- Don't dominate 营销

### Announcement Tactics

**Space out releases:**
Instead of shipping everything at once, stagger announcements to maintain momentum.

**Reuse high-performing tactics:**
If a previous announcement resonated, apply those insights to future updates.

**Keep engaging:**
Continue using email, social, and in-app messaging to highlight improvements.

**Signal active development:**
Even small changelog updates remind 客户 your 产品 is evolving. This builds retention and word-of-mouth—客户 feel confident you'll be around.

---

## Launch Checklist

### Pre-Launch
- [ ] 落地页 with clear value proposition
- [ ] Email capture / waitlist signup
- [ ] Early access list built
- [ ] Owned channels established (email, blog, community)
- [ ] Rented channel presence (social profiles optimized)
- [ ] Borrowed channel opportunities identified (podcasts, influencers)
- [ ] 产品 Hunt listing prepared (if using)
- [ ] Launch assets created (screenshots, demo 视频, GIFs)
- [ ] Onboarding flow ready
- [ ] 分析/跟踪 in place

### Launch Day
- [ ] Announcement email to list
- [ ] Blog post published
- [ ] Social posts scheduled and posted
- [ ] 产品 Hunt listing live (if using)
- [ ] In-app announcement for existing users
- [ ] Website banner/notification active
- [ ] Team ready to engage and respond
- [ ] Monitor for issues and feedback

### Post-Launch
- [ ] Onboarding 邮件序列 active
- [ ] Follow-up with engaged prospects
- [ ] Roundup email includes announcement
- [ ] Comparison pages published
- [ ] Interactive demo created
- [ ] Gather and act on feedback
- [ ] Plan next launch moment

---

## Task-Specific Questions

1. What are you launching? (New 产品, major feature, minor update)
2. What's your current 受众 size and engagement?
3. What owned channels do you have? (Email list size, blog traffic, community)
4. What's your timeline for launch?
5. Have you launched before? What worked/didn't work?
6. Are you considering 产品 Hunt? What's your preparation status?

---

## Related 技能

- **marketing-ideas**: For additional launch tactics (#22 产品 Hunt, #23 Early Access Referrals)
- **email-sequence**: For launch and onboarding 邮件序列s
- **page-cro**: For optimizing launch 落地页s
- **营销-psychology**: For psychology behind waitlists and exclusivity
- **programmatic-seo**: For comparison pages mentioned in post-launch
- **sales-enablement**: For launch sales collateral and enablement materials
