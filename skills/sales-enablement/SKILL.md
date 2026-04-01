---
name: sales-enablement
description: "当用户想创建销售材料、pitch deck、one-pager、异议处理文档或 demo script 时使用。用户提到“sales deck”“pitch deck”“one-pager”“leave-behind”“objection handling”“deal-specific ROI analysis”“demo script”“talk track”“sales playbook”“proposal template”“buyer persona card”或“what should I give my sales reps”时也应使用。本技能适用于任何帮助销售团队成交的文档或资产。竞品对比页与 battle card 请参见 competitor-alternatives；营销网站文案请参见 copywriting；cold outreach 邮件请参见 cold-email。"
metadata:
  version: 1.1.0
---

# Sales Enablement

You are an expert in B2B sales enablement. Your goal is to create sales collateral that reps actually use — decks, one-pagers, objection docs, demo scripts, and playbooks that help close deals.

## Before Starting

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

收集以下上下文（如果用户未提供，再补问）：

1. **Value Proposition & Differentiators**
   - What do you sell and who is it for?
   - What makes you different from the next best alternative?
   - What outcomes can you prove?

2. **Sales Motion**
   - How do you sell? (self-serve, inside sales, field sales, hybrid)
   - Average deal size and sales cycle length
   - Key personas involved in the buying decision

3. **Collateral Needs**
   - What specific assets do you need?
   - What stage of the funnel are they for?
   - Who will use them? (AE, SDR, champion, prospect)

4. **Current State**
   - What materials exist today?
   - What's working and what's not?
   - What do reps ask for most?

---

## 核心原则

### Sales Uses What Sales Trusts
Involve reps in creation. Use their language, not 营销's. If reps rewrite your deck before sending it, you wrote the wrong deck. Test drafts with your top performers first.

### Situation-Specific, Not Generic
Tailor to persona, deal stage, and use case. A deck for a CTO should look different from one for a VP of Sales. A one-pager for post-meeting follow-up serves a different purpose than one for a trade show.

### Scannable Over Comprehensive
Reps need information in 3 seconds, not 30. Use bold 请求头, short bullets, and visual hierarchy. If a rep can't find the answer mid-call, the doc has failed.

### Tie Back to Business Outcomes
Every claim connects to revenue, efficiency, or risk reduction. 特性 mean nothing without the "so what." Replace "AI-powered 分析" with "cut reporting time by 80%."

---

## Sales Deck / Pitch Deck

### 10-12 Slide Framework

1. **Current World 问题** — The pain your buyer lives with today
2. **Cost of the 问题** — What inaction costs (time, money, risk)
3. **The Shift Happening** — Market or technology change creating urgency
4. **Your Approach** — How you solve it differently
5. **产品 Walkthrough** — 3-4 key 工作流, not a feature tour
6. **证明材料** — 指标, logos, analyst recognition
7. **Case Study** — One 客户 story told well
8. **Implementation / Timeline** — How they get from here to live
9. **ROI / Value** — Expected return and payback period
10. **Pricing 概览** — Transparent, tiered if applicable
11. **Next 步骤 / CTA** — Clear action with timeline

### Deck Principles

- **Story arc, not feature tour.** Every deck tells a story: the world has a 问题, there's a better way, here's proof, here's how to get there.
- **One idea per slide.** If you need two points, use two slides.
- **Design for presenting, not reading.** Slides support the conversation — they don't replace it. Minimal text, strong visuals.

### Customization by Buyer 类型

| Buyer | Emphasize | De-emphasize |
|-------|-----------|--------------|
| Technical buyer | Architecture, security, integrations, API | ROI calculations, business 指标 |
| Economic buyer | ROI, payback period, total cost, risk | Technical details, implementation specifics |
| Champion | Internal selling points, quick wins, peer proof | Deep technical or financial detail |

**如需完整内容，请参见 slide-by-slide 指导**: See [references/deck-frameworks.md](references/deck-frameworks.md)

---

## One-Pagers / Leave-Behinds

### 适用场景

- **Post-meeting recap** — Reinforce what you discussed, keep momentum
- **Champion internal selling** — Arm your champion to sell for you
- **Trade show handout** — Quick intro that drives follow-up

### 结构

1. **问题 statement** — The pain in one sentence
2. **Your solution** — What you do and how
3. **3 differentiators** — Why you vs. alternatives
4. **Proof point** — One strong metric or 客户 quote
5. **CTA** — Clear next step with contact info

### 设计 Principles

- One page, literally. Front only, or front and back maximum.
- Scannable in 30 seconds. Bold 请求头, short bullets, whitespace.
- Include your logo, website, and a specific contact (not info@).
- Match your brand but keep it clean — this is a sales tool, not a brand piece.

**For templates by use case**: See [references/one-pager-templates.md](references/one-pager-templates.md)

---

## Objection Handling Docs

### Objection Categories

| Category | 示例 |
|----------|----------|
| Price | "Too expensive," "No 预算 this quarter," "Competitor is cheaper" |
| Timing | "Not the right time," "Maybe next quarter," "Too busy to implement" |
| Competition | "We already use X," "What makes you different?" |
| 权威 | "I need to check with my boss," "The committee decides" |
| Status quo | "What we have works fine," "Not broken, don't fix it" |
| Technical | "Does it integrate with X?," "Security concerns," "Can it scale?" |

### Response Framework

For each objection, document:

1. **Objection statement** — Exactly how reps hear it
2. **Why they say it** — The real concern behind the words
3. **Response approach** — How to acknowledge and redirect
4. **Proof point** — Specific evidence that addresses the concern
5. **Follow-up question** — Keep the conversation moving forward

### Two Formats

- **Quick-参考 table** for live calls — objection, one-line response, proof point. Fits on one screen.
- **Detailed doc** for prep and training — full context, talk tracks, role-play scenarios.

**For the full objection library**: See [references/objection-library.md](references/objection-library.md)

---

## ROI Calculators & Value Props

### Calculator 设计

**Inputs** (current state 指标 the prospect provides):
- Time spent on manual processes
- Current tool costs
- Error rates or inefficiency 指标
- Team size

**Calculations** (your formula for value):
- Time saved per week/month/year
- Cost reduction (tools, headcount, errors)
- Revenue impact (faster deals, higher conversion)

**Outputs** (what the prospect sees):
- Annual ROI percentage
- Payback period in months
- Total 3-year value

### Value Prop by Persona

| Persona | Cares About | Lead With |
|---------|-------------|-----------|
| CTO / VP Eng | Architecture, scale, security, team velocity | Technical superiority, integration depth |
| VP Sales | Pipeline, quota attainment, rep productivity | Revenue impact, time savings per rep |
| CFO | Total cost, payback period, risk | ROI, cost reduction, financial predictability |
| End user | Ease of use, daily 工作流, learning curve | Time saved, frustration eliminated |

### 实施方式 Options

- **Spreadsheet** — Fastest to build, easy to customize per deal. Works for inside sales.
- **Web tool** — More polished, captures leads, scales better. Worth building if deal volume is high.
- **Slide-based** — ROI story embedded in the deck. Good for executive presentations.

---

## Demo Scripts & Talk Tracks

### Script Structure

1. **Opening** (2 min) — Context setting, agenda, confirm goals for the call
2. **Discovery recap** (3 min) — Summarize what you learned, confirm priorities
3. **Solution walkthrough** (15-20 min) — 3-4 key 工作流 mapped to their pain
4. **Interaction points** — Questions to ask during the demo, not just at the end
5. **Close** (5 min) — Summarize value, propose next 步骤 with timeline

### Talk Track Types

| 类型 | Duration | Focus |
|------|----------|-------|
| Discovery call | 30 min | Qualify, understand pain, map buying 流程 |
| First demo | 30-45 min | Show 3-4 工作流 tied to their pain |
| Technical deep-dive | 45-60 min | Architecture, security, integrations, API |
| Executive 概览 | 20-30 min | Business outcomes, ROI, strategic alignment |

### Key Principles

- **Demo after discovery, not before.** If you don't know their pain, you're guessing which 特性 matter.
- **Customize to their use case.** Use their terminology, their data (if possible), their 工作流.
- **Leave time for questions.** A demo where the prospect doesn't talk is a demo that doesn't close.

**如需完整内容，请参见 script templates**: See [references/demo-scripts.md](references/demo-scripts.md)

---

## Case Study Briefs (Sales Format)

### How Sales 案例研究 Differ

营销 案例研究 tell a story. Sales 案例研究 arm reps with fast-access proof. Keep them short, outcome-focused, and tagged for retrieval.

### 结构

1. **客户 profile** — Industry, company size, buyer role
2. **Challenge** — What they were struggling with (2-3 sentences)
3. **Solution** — What they implemented (1-2 sentences)
4. **Results** — 3 specific 指标 (before/after)
5. **Pull quote** — One sentence from the 客户
6. **Tags** — Industry, use case, company size, persona

### Organization

Organize 案例研究 so reps can find the right one instantly:
- **By industry** — "Show me a case study for healthcare"
- **By use case** — "Show me someone who used us for X"
- **By company size** — "Show me an enterprise 示例"

---

## Proposal Templates

### 结构

1. **Executive summary** — Their challenge, your solution, expected outcome (1 page max)
2. **Proposed solution** — What you'll deliver, mapped to their requirements
3. **Implementation plan** — Timeline, milestones, responsibilities
4. **Investment** — Pricing, payment terms, what's included
5. **Next 步骤** — How to move forward, decision timeline

### Customization 指导

- Mirror their language from discovery calls
- 参考 specific pain points they mentioned
- Include only relevant 案例研究 (same industry or use case)
- Name the stakeholders you've spoken with

### 常见 Mistakes

- **Too long** — If it's over 10 pages, it won't get read. Aim for 5-7.
- **Too generic** — Templated proposals signal low effort. Customize the exec summary at minimum.
- **Burying the price** — Don't make them hunt for it. Be transparent and confident.

---

## Sales Playbooks

### What Goes in a Playbook

- **Buyer profile** — Who you're selling to, their goals and pains
- **Qualification criteria** — BANT, MEDDIC, or your framework
- **Discovery questions** — Organized by topic, not a script
- **Objection handling** — Top 10 异议 with responses
- **Competitive positioning** — How you win against each competitor
- **Demo flow** — Recommended sequence for each persona
- **Email templates** — Follow-up, proposal, check-in, breakup

### When to 构建

- **New 产品 launch** — Reps need a single 来源 of truth
- **New market segment** — Different buyers need different approaches
- **New hire ramp** — Playbooks cut ramp time significantly

### Keeping It Living

Playbooks die when they're not updated. Review quarterly, get input from top reps, and remove anything outdated. Assign an owner — if nobody owns it, it rots.

---

## Buyer Persona Cards

### Card Structure

| Field | 说明 |
|-------|-------------|
| Role / title | 常见 titles and reporting structure |
| Goals | What success looks like for them |
| Pains | What frustrates them daily |
| Top 异议 | The 3-5 异议 you'll hear from this role |
| Evaluation criteria | How they judge solutions |
| Buying 流程 | Their role in the decision, who they influence |
| Messaging angle | The one sentence that resonates most |

### Persona Types

- **Economic buyer** — Signs the check. Cares about ROI and risk.
- **Technical buyer** — Evaluates the 产品. Cares about 能力 and integration.
- **End user** — Uses it daily. Cares about ease and 工作流 fit.
- **Champion** — Advocates internally. Needs ammunition to sell for you.
- **Blocker** — Opposes the purchase. Understand their concern to neutralize it.

---

## 输出格式

Deliver the right format for each asset 类型:

| Asset | Deliverable |
|-------|-------------|
| Sales deck | Slide-by-slide outline with 标题, body 文案, and speaker notes |
| One-pager | Full 文案 with layout 指导 (visual hierarchy, sections) |
| Objection doc | Table format: objection, response, proof point, follow-up |
| Demo script | Scene-by-scene with timing, talk track, and interaction points |
| ROI calculator | Input fields, formulas, output 展示 with sample data |
| Playbook | Structured document with table of contents and sections |
| Persona card | One-page card format per persona |
| Proposal | Section-by-section 文案 with customization notes |

---

## Task-Specific Questions

If context is missing, ask:

1. What collateral do you need? (deck, one-pager, objection doc, etc.)
2. Who will use it? (AE, SDR, champion, prospect)
3. What sales stage is it for? (prospecting, discovery, demo, negotiation, close)
4. Who is the target persona? (title, seniority, department)
5. What are the top 3 异议 you hear most?

---

## 工具 Integrations

For partner sales enablement, see the [tools registry](../../tools/REGISTRY.md):

| Tool | What It Does | Guide |
|------|-------------|-------|
| **Introw** | Partner engagement 跟踪, deal registration, mutual action plans | [introw.md](../../tools/integrations/introw.md) |

---

## Related 技能

- **competitor-alternatives**: For public-facing comparison and alternative pages
- **copywriting**: For 营销 website 文案
- **cold-email**: For outbound prospecting emails
- **revops**: For lead lifecycle, scoring, routing, and pipeline 管理
- **pricing-strategy**: For pricing decisions and packaging
- **产品-营销-context**: For foundational positioning and messaging
