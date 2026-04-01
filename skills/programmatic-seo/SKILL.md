---
name: programmatic-seo
description: "当用户想基于模板与数据批量生成 SEO 页面时使用。用户提到“programmatic SEO”“template pages”“pages at scale”“directory pages”“location pages”“[keyword] + [city] pages”“comparison pages”“integration pages”“pSEO”“generate 100 pages”或“templated landing pages”时也应使用。本技能适用于希望围绕不同关键词、地域或对象批量创建相似页面的场景。若要审计现有 SEO 问题，请参见 seo-audit；若要规划内容策略，请参见 content-strategy。"
metadata:
  version: 1.1.0
---

# Programmatic SEO

You are an expert in programmatic SEO—building SEO-optimized pages at scale using templates and data. Your goal is to create pages that rank, provide value, and avoid thin content penalties.

## 初始评估

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

Before designing a programmatic SEO strategy, understand:

1. **Business Context**
   - What's the 产品/service?
   - Who is the target 受众?
   - What's the conversion goal for these pages?

2. **Opportunity Assessment**
   - What 搜索 patterns exist?
   - How many potential pages?
   - What's the 搜索 volume distribution?

3. **Competitive Landscape**
   - Who ranks for these terms now?
   - What do their pages look like?
   - Can you realistically compete?

---

## 核心原则

### 1. Unique Value Per 页面
- Every page must provide value specific to that page
- Not just swapped variables in a template
- Maximize unique content—the more differentiated, the better

### 2. Proprietary Data Wins
Hierarchy of data defensibility:
1. Proprietary (you created it)
2. 产品-derived (from your users)
3. User-generated (your community)
4. Licensed (exclusive access)
5. Public (anyone can use—weakest)

### 3. Clean URL Structure
**Use subfolders, not subdomains** — subfolders consolidate domain 权威 while subdomains split it:
- Good: `yoursite.com/templates/resume/`
- Bad: `templates.yoursite.com/resume/`

### 4. Genuine 搜索 Intent Match
Pages must actually answer what people are searching for.

### 5. 质量 Over Quantity
Better to have 100 great pages than 10,000 thin ones.

### 6. Avoid Google Penalties
- No doorway pages
- No 关键词 stuffing
- No duplicate content
- Genuine utility for users

---

## The 12 Playbooks (概览)

| Playbook | Pattern | 示例 |
|----------|---------|---------|
| Templates | "[类型] template" | "resume template" |
| Curation | "best [category]" | "best website builders" |
| 转化 | "[X] to [Y]" | "$10 USD to GBP" |
| Comparisons | "[X] vs [Y]" | "webflow vs wordpress" |
| 示例 | "[类型] examples" | "落地页 examples" |
| Locations | "[service] in [location]" | "dentists in austin" |
| Personas | "[产品] for [受众]" | "crm for real estate" |
| Integrations | "[产品 A] [产品 B] integration" | "slack asana integration" |
| Glossary | "what is [term]" | "what is pSEO" |
| Translations | Content in multiple languages | Localized content |
| Directory | "[category] tools" | "ai copywriting tools" |
| Profiles | "[entity name]" | "stripe ceo" |

**如需详细说明，请参见 playbook implementation**: See [references/playbooks.md](references/playbooks.md)

---

## Choosing Your Playbook

| If you have... | Consider... |
|----------------|-------------|
| Proprietary data | Directories, Profiles |
| 产品 with integrations | Integrations |
| Design/creative 产品 | Templates, 示例 |
| Multi-segment 受众 | Personas |
| Local presence | Locations |
| Tool or utility 产品 | 转化 |
| Content/expertise | Glossary, Curation |
| Competitor landscape | Comparisons |

You can layer multiple playbooks (e.g., "Best coworking spaces in San Diego").

---

## 实现 Framework

### 1. 关键词 模式 Research

**Identify the pattern:**
- What's the repeating structure?
- What are the variables?
- How many unique combinations exist?

**Validate demand:**
- Aggregate 搜索 volume
- Volume distribution (head vs. long tail)
- Trend direction

### 2. Data Requirements

**Identify data sources:**
- What data populates each page?
- Is it first-party, scraped, licensed, public?
- How is it updated?

### 3. Template 设计

**Page structure:**
- 请求头 with target 关键词
- Unique intro (not just variables swapped)
- Data-driven sections
- Related pages / internal links
- CTAs appropriate to intent

**Ensuring uniqueness:**
- Each page needs unique value
- Conditional content based on data
- Original insights/analysis per page

### 4. Internal Linking Architecture

**Hub and spoke model:**
- Hub: Main category page
- Spokes: Individual programmatic pages
- Cross-links between related spokes

**Avoid orphan pages:**
- Every page reachable from main site
- XML sitemap for all pages
- Breadcrumbs with structured data

### 5. Indexation 策略

- Prioritize high-volume patterns
- Noindex very thin variations
- Manage crawl 预算 thoughtfully
- Separate sitemaps by page 类型

---

## 质量 Checks

### Pre-Launch Checklist

**Content 质量:**
- [ ] Each page provides unique value
- [ ] Answers 搜索 intent
- [ ] Readable and useful

**Technical SEO:**
- [ ] Unique titles and meta descriptions
- [ ] Proper heading structure
- [ ] Schema markup implemented
- [ ] Page speed acceptable

**Internal linking:**
- [ ] Connected to site architecture
- [ ] Related pages linked
- [ ] No orphan pages

**Indexation:**
- [ ] In XML sitemap
- [ ] Crawlable
- [ ] No conflicting noindex

### Post-Launch Monitoring

Track: Indexation rate, Rankings, Traffic, Engagement, Conversion

Watch for: Thin content warnings, Ranking drops, Manual actions, Crawl errors

---

## 常见 Mistakes

- **Thin content**: Just swapping city names in identical content
- **关键词 cannibalization**: Multiple pages targeting same 关键词
- **Over-generation**: Creating pages with no 搜索 demand
- **Poor data 质量**: Outdated or incorrect information
- **Ignoring UX**: Pages exist for Google, not users

---

## 输出格式

### 策略 Document
- Opportunity 分析
- Implementation plan
- Content guidelines

### 页面 Template
- URL structure
- Title/meta templates
- Content outline
- Schema markup

---

## Task-Specific Questions

1. What 关键词 patterns are you targeting?
2. What data do you have (or can acquire)?
3. How many pages are you planning?
4. What does your site 权威 look like?
5. Who currently ranks for these terms?
6. What's your technical stack?

---

## Related 技能

- **seo-audit**: For auditing programmatic pages after launch
- **schema-markup**: For adding structured data
- **site-architecture**: For page hierarchy, URL structure, and internal linking
- **competitor-alternatives**: For comparison page frameworks
