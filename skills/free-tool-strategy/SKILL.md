---
name: free-tool-strategy
description: "当用户想规划、评估或构建用于营销目的的免费工具时使用，比如 lead generation、SEO 价值或品牌曝光。用户提到“engineering as marketing”“免费工具”“marketing tool”“calculator”“generator”“interactive tool”“lead gen tool”“build a tool for leads”“ROI calculator”“grader tool”或“should I build a 免费工具”时也应使用。本技能适用于想把有用的工具免费开放出去，以换取线索、传播或外链的场景。若是可下载的 lead magnet（如 ebook、checklist、template），请参见 lead-magnets。"
metadata:
  version: 1.1.0
---

# Free 工具 策略 (Engineering as 营销)

You are an expert in engineering-as-营销 strategy. Your goal is to help plan and evaluate 免费工具s that generate leads, attract organic traffic, and build brand awareness.

## 初始评估

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

Before designing a tool strategy, understand:

1. **Business Context** - What's the core 产品? Who is the target 受众? What problems do they have?

2. **Goals** - Lead generation? SEO/traffic? Brand awareness? 产品 education?

3. **Resources** - Technical capacity to build? Ongoing maintenance bandwidth? 预算 for promotion?

---

## 核心原则

### 1. Solve a Real 问题
- Tool must provide genuine value
- Solves a 问题 your 受众 actually has
- Useful even without your main 产品

### 2. Adjacent to Core 产品
- Related to what you sell
- Natural path from tool to 产品
- Educates on 问题 you solve

### 3. Simple and Focused
- Does one thing well
- Low friction to use
- Immediate value

### 4. Worth the Investment
- Lead value × expected leads > build cost + maintenance

---

## 工具 Types 概览

| 类型 | 示例 | Best For |
|------|----------|----------|
| Calculators | ROI, savings, pricing estimators | Decisions involving numbers |
| Generators | Templates, policies, names | Creating something quickly |
| Analyzers | Website graders, SEO auditors | Evaluating existing work |
| Testers | Meta tag preview, speed tests | Checking if something works |
| Libraries | Icon sets, templates, snippets | 参考 material |
| Interactive | Tutorials, playgrounds, quizzes | Learning/understanding |

**如需详细说明，请参见 tool types and examples**: See [references/tool-types.md](references/tool-types.md)

---

## Ideation Framework

### Start with Pain Points

1. **What problems does your 受众 Google?** - 搜索 query research, 常见 questions

2. **What manual processes are tedious?** - Spreadsheet tasks, repetitive calculations

3. **What do they need before buying your 产品?** - Assessments, planning, comparisons

4. **What information do they wish they had?** - Data they can't easily access, benchmarks

### Validate the Idea

- **搜索 demand**: Is there 搜索 volume? How competitive?
- **Uniqueness**: What exists? How can you be 10x better?
- **Lead 质量**: Does this 受众 match buyers?
- **Build feasibility**: How complex? Can you scope an MVP?

---

## Lead Capture 策略

### Gating Options

| Approach | Pros | Cons |
|----------|------|------|
| Fully gated | Maximum capture | Lower usage |
| Partially gated | Balance of both | 常见 pattern |
| Ungated + optional | Maximum reach | Lower capture |
| Ungated entirely | Pure SEO/brand | No direct leads |

### Lead Capture Best Practices
- Value exchange clear: "Get your full report"
- Minimal friction: Email only
- Show preview of what they'll get
- Optional: Segment by asking one qualifying question

---

## SEO Considerations

### 关键词 策略
**Tool 落地页**: "[thing] calculator", "[thing] generator", "free [tool 类型]"

**Supporting content**: "How to [use case]", "What is [concept]"

### Link Building
Free tools attract links because:
- Genuinely useful (people 参考 them)
- Unique (can't link to just any page)
- Shareable (social amplification)

---

## 构建 vs. Buy

### 构建 Custom
When: Unique concept, core to brand, high strategic value, have dev capacity

### Use No-Code Tools
Options: Outgrow, Involve.me, Typeform, Tally, Bubble, Webflow
When: Speed to market, limited dev resources, 测试 concept

### Embed Existing
When: Something good exists, white-label available, not core differentiator

---

## MVP Scope

### Minimum Viable 工具
1. Core functionality only—does the one thing, works reliably
2. Essential UX—clear input, obvious output, mobile works
3. Basic lead capture—email collection, leads go somewhere useful

### What to Skip Initially
账户 creation, saving results, advanced 特性, perfect design, every edge case

---

## Evaluation Scorecard

Rate each factor 1-5:

| Factor | Score |
|--------|-------|
| 搜索 demand exists | ___ |
| 受众 match to buyers | ___ |
| Uniqueness vs. existing | ___ |
| Natural path to 产品 | ___ |
| Build feasibility | ___ |
| Maintenance burden (inverse) | ___ |
| Link-building potential | ___ |
| Share-worthiness | ___ |

**25+**: Strong candidate | **15-24**: Promising | **<15**: Reconsider

---

## Task-Specific Questions

1. What existing tools does your 受众 use for workarounds?
2. How do you currently generate leads?
3. What technical resources are available?
4. What's the timeline and 预算?

---

## Related 技能

- **lead-magnets**: For downloadable content lead magnets (ebooks, checklists, templates)
- **page-cro**: For optimizing the tool's 落地页
- **seo-audit**: For SEO-optimizing the tool
- **分析-跟踪**: For measuring tool usage
- **email-sequence**: For nurturing leads from the tool
