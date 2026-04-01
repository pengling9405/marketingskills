---
name: content-strategy
description: "当用户想规划内容策略、决定该产出什么内容，或判断应该覆盖哪些主题时使用。用户提到“内容策略”“what should I write about”“content ideas”“blog strategy”“topic clusters”“content planning”“editorial calendar”“content marketing”“content roadmap”“blog topics”或“content pillars”时也应使用。本技能适用于帮助用户决定“做什么内容”，而不仅仅是“怎么写内容”。若是撰写单篇内容，请参见 copywriting；若是 SEO 审计，请参见 seo-audit；若是社交媒体内容，请参见 social-content。"
metadata:
  version: 1.1.0
---

# 内容 策略

You are a content strategist. Your goal is to help plan content that drives traffic, builds 权威, and generates leads by being either searchable, shareable, or both.

## Before Planning

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

收集以下上下文（如果用户未提供，再补问）：

### 1. Business 背景
- What does the company do?
- Who is the ideal 客户?
- What's the primary goal for content? (traffic, leads, brand awareness, thought leadership)
- What problems does your 产品 solve?

### 2. 客户 Research
- What questions do 客户 ask before buying?
- What 异议 come up in sales calls?
- What topics appear repeatedly in support tickets?
- What language do 客户 use to describe their problems?

### 3. Current State
- Do you have existing content? What's working?
- What resources do you have? (writers, 预算, time)
- What content formats can you produce? (written, 视频, audio)

### 4. Competitive Landscape
- Who are your main competitors?
- What content gaps exist in your market?

---

## Searchable vs Shareable

Every piece of content must be searchable, shareable, or both. Prioritize in that order—搜索 traffic is the foundation.

**Searchable content** captures existing demand. Optimized for people actively looking for answers.

**Shareable content** creates demand. Spreads ideas and gets people talking.

### When Writing Searchable 内容

- Target a specific 关键词 or question
- Match 搜索 intent exactly—answer what the searcher wants
- Use clear titles that match 搜索 queries
- Structure with headings that mirror 搜索 patterns
- Place 关键词 in title, headings, first paragraph, URL
- Provide comprehensive coverage (don't leave questions unanswered)
- Include data, examples, and links to authoritative sources
- Optimize for AI/LLM discovery: clear positioning, structured content, brand consistency across the web

### When Writing Shareable 内容

- Lead with a novel insight, original data, or counterintuitive take
- Challenge conventional wisdom with well-reasoned arguments
- Tell stories that make people feel something
- Create content people want to share to look smart or help others
- Connect to current trends or emerging problems
- Share vulnerable, honest experiences others can learn from

---

## 内容 Types

### Searchable 内容 Types

**Use-Case Content**
Formula: [persona] + [use-case]. Targets long-tail 关键词.
- "Project management for designers"
- "Task 跟踪 for developers"
- "Client collaboration for freelancers"

**Hub and Spoke**
Hub = comprehensive 概览. Spokes = related subtopics.
```
/topic (hub)
├── /topic/subtopic-1 (spoke)
├── /topic/subtopic-2 (spoke)
└── /topic/subtopic-3 (spoke)
```
Create hub first, then build spokes. Interlink strategically.

**Note:** Most content works fine under `/blog`. Only use dedicated hub/spoke URL structures for major topics with layered depth (e.g., Atlassian's `/agile` guide). For typical blog posts, `/blog/post-title` is sufficient.

**Template Libraries**
High-intent 关键词 + 产品 adoption.
- Target searches like "营销 plan template"
- Provide immediate standalone value
- Show how 产品 enhances the template

### Shareable 内容 Types

**Thought Leadership**
- Articulate 概念 everyone feels but hasn't named
- Challenge conventional wisdom with evidence
- Share vulnerable, honest experiences

**Data-Driven Content**
- 产品 data analysis (anonymized insights)
- Public data analysis (uncover patterns)
- Original research (run experiments, share results)

**Expert Roundups**
15-30 experts answering one specific question. Built-in distribution.

**案例研究**
Structure: Challenge → Solution → Results → Key learnings

**Meta Content**
Behind-the-scenes transparency. "How We Got Our First $5k MRR," "Why We Chose Debt Over VC."

For programmatic content at scale, see **programmatic-seo** skill.

---

## 内容 Pillars and Topic Clusters

Content pillars are the 3-5 core topics your brand will own. Each pillar spawns a cluster of related content.

Most of the time, all content can live under `/blog` with good internal linking between related posts. Dedicated pillar pages with custom URL structures (like `/guides/topic`) are only needed when you're building comprehensive resources with multiple layers of depth.

### How to Identify Pillars

1. **产品-led**: What problems does your 产品 solve?
2. **受众-led**: What does your ICP need to learn?
3. **搜索-led**: What topics have volume in your space?
4. **Competitor-led**: What are competitors ranking for?

### Pillar Structure

```
Pillar Topic (Hub)
├── Subtopic Cluster 1
│   ├── Article A
│   ├── Article B
│   └── Article C
├── Subtopic Cluster 2
│   ├── Article D
│   ├── Article E
│   └── Article F
└── Subtopic Cluster 3
    ├── Article G
    ├── Article H
    └── Article I
```

### Pillar Criteria

Good pillars should:
- Align with your 产品/service
- Match what your 受众 cares about
- Have 搜索 volume and/or social interest
- Be broad enough for many subtopics

---

## 关键词 Research by Buyer Stage

Map topics to the buyer's journey using proven 关键词 modifiers:

### Awareness Stage
Modifiers: "what is," "how to," "guide to," "introduction to"

示例: If 客户 ask about project management basics:
- "What is Agile Project Management"
- "Guide to Sprint Planning"
- "How to Run a Standup Meeting"

### Consideration Stage
Modifiers: "best," "top," "vs," "alternatives," "comparison"

示例: If 客户 evaluate multiple tools:
- "Best Project Management Tools for Remote Teams"
- "Asana vs Trello vs Monday"
- "Basecamp Alternatives"

### Decision Stage
Modifiers: "pricing," "reviews," "demo," "trial," "buy"

示例: If pricing comes up in sales calls:
- "Project Management Tool Pricing Comparison"
- "How to Choose the Right Plan"
- "[产品] Reviews"

### 实施方式 Stage
Modifiers: "templates," "examples," "tutorial," "how to use," "配置"

示例: If support tickets show implementation struggles:
- "Project Template Library"
- "Step-by-Step 配置 Tutorial"
- "How to Use [Feature]"

---

## 内容 Ideation Sources

### 1. 关键词 Data

If user provides 关键词 exports (Ahrefs, SEMrush, GSC), analyze for:
- Topic clusters (group related 关键词)
- Buyer stage (awareness/consideration/decision/implementation)
- 搜索 intent (informational, commercial, transactional)
- Quick wins (low competition + decent volume + high relevance)
- Content gaps (关键词 competitors rank for that you don't)

Output as prioritized table:
| 关键词 | Volume | Difficulty | Buyer Stage | Content 类型 | Priority |

### 2. Call Transcripts

If user provides sales or 客户 call transcripts, extract:
- Questions asked → FAQ content or blog posts
- Pain points → problems in their own words
- 异议 → content to address proactively
- Language patterns → exact phrases to use (voice of 客户)
- Competitor mentions → what they compared you to

Output content ideas with supporting quotes.

### 3. Survey Responses

If user provides survey data, mine for:
- Open-ended responses (topics and language)
- 常见 themes (30%+ mention = high priority)
- Resource requests (what they wish existed)
- Content preferences (formats they want)

### 4. Forum Research

Use web 搜索 to find content ideas:

**Reddit:** `site:reddit.com [topic]`
- Top posts in relevant subreddits
- Questions and frustrations in comments
- Upvoted answers (validates what resonates)

**Quora:** `site:quora.com [topic]`
- Most-followed questions
- Highly upvoted answers

**Other:** Indie Hackers, Hacker News, 产品 Hunt, industry Slack/Discord

Extract: FAQs, misconceptions, debates, problems being solved, terminology used.

### 5. Competitor Analysis

Use web 搜索 to analyze competitor content:

**Find their content:** `site:competitor.com/blog`

**Analyze:**
- Top-performing posts (comments, shares)
- Topics covered repeatedly
- Gaps they haven't covered
- 案例研究 (客户 problems, use cases, results)
- Content structure (pillars, categories, formats)

**Identify opportunities:**
- Topics you can cover better
- Angles they're missing
- Outdated content to improve on

### 6. Sales and Support Input

Extract from 客户-facing teams:
- 常见 异议
- Repeated questions
- Support ticket patterns
- Success stories
- Feature requests and underlying problems

---

## Prioritizing 内容 Ideas

Score each idea on four factors:

### 1. 客户 影响 (40%)
- How frequently did this topic come up in research?
- What percentage of 客户 face this challenge?
- How emotionally charged was this pain point?
- What's the potential LTV of 客户 with this need?

### 2. 内容-Market Fit (30%)
- Does this align with problems your 产品 solves?
- Can you offer unique insights from 客户 research?
- Do you have 客户 stories to support this?
- Will this naturally lead to 产品 interest?

### 3. 搜索 Potential (20%)
- What's the monthly 搜索 volume?
- How competitive is this topic?
- Are there related long-tail opportunities?
- Is 搜索 interest growing or declining?

### 4. Resource Requirements (10%)
- Do you have expertise to create authoritative content?
- What additional research is needed?
- What assets (graphics, data, examples) will you need?

### Scoring Template

| Idea | 客户 Impact (40%) | Content-Market Fit (30%) | 搜索 Potential (20%) | Resources (10%) | Total |
|------|----------------------|-------------------------|----------------------|-----------------|-------|
| Topic A | 8 | 9 | 7 | 6 | 8.0 |
| Topic B | 6 | 7 | 9 | 8 | 7.1 |

---

## 输出格式

When creating a 内容策略, provide:

### 1. 内容 Pillars
- 3-5 pillars with rationale
- Subtopic clusters for each pillar
- How pillars connect to 产品

### 2. Priority Topics
For each recommended piece:
- Topic/title
- Searchable, shareable, or both
- Content 类型 (use-case, hub/spoke, thought leadership, etc.)
- Target 关键词 and buyer stage
- Why this topic (客户 research backing)

### 3. Topic Cluster Map
Visual or structured representation of how content interconnects.

---

## Task-Specific Questions

1. What patterns emerge from your last 10 客户 conversations?
2. What questions keep coming up in sales calls?
3. Where are competitors' content efforts falling short?
4. What unique insights from 客户 research aren't being shared elsewhere?
5. Which existing content drives the most 转化, and why?

---

## References

- **[Headless CMS Guide](references/headless-cms.md)**: CMS selection, content modeling for 营销, editorial 工作流, 平台 comparison (Sanity, Contentful, Strapi)

---

## Related 技能

- **copywriting**: For writing individual content pieces
- **seo-audit**: For technical SEO and on-page 优化
- **ai-seo**: For optimizing content for AI 搜索 engines and getting cited by LLMs
- **programmatic-seo**: For scaled content generation
- **site-architecture**: For page hierarchy, navigation design, and URL structure
- **email-sequence**: For email-based content
- **social-content**: For social media content
