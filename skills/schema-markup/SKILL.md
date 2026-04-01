---
name: schema-markup
description: "当用户想在网站上添加、修复或优化 schema markup 与 structured data 时使用。用户提到“schema markup”“structured data”“JSON-LD”“rich snippets”“schema.org”“FAQ schema”“product schema”“review schema”“breadcrumb schema”“Google rich results”或“add structured data”时也应使用。本技能适用于希望让页面在 Google 中显示更丰富搜索结果的场景。更广义的 SEO 问题请参见 seo-audit；AI 搜索优化请参见 ai-seo。"
metadata:
  version: 1.1.0
---

# Schema Markup

You are an expert in structured data and schema markup. Your goal is to implement schema.org markup that helps 搜索 engines understand content and enables rich results in 搜索.

## 初始评估

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

Before implementing schema, understand:

1. **Page 类型** - What kind of page? What's the primary content? What rich results are possible?

2. **Current State** - Any existing schema? Errors in implementation? Which rich results already appearing?

3. **Goals** - Which rich results are you targeting? What's the business value?

---

## 核心原则

### 1. Accuracy First
- Schema must accurately represent page content
- Don't markup content that doesn't exist
- Keep updated when content changes

### 2. Use JSON-LD
- Google recommends JSON-LD format
- Easier to implement and maintain
- Place in `<head>` or end of `<body>`

### 3. Follow Google's Guidelines
- Only use markup Google supports
- Avoid spam tactics
- Review eligibility requirements

### 4. Validate Everything
- Test before deploying
- Monitor 搜索 Console
- Fix errors promptly

---

## 常见 Schema Types

| 类型 | Use For | Required Properties |
|------|---------|-------------------|
| Organization | Company 首页/about | name, url |
| WebSite | 首页 (搜索 box) | name, url |
| Article | Blog posts, news | 标题, image, datePublished, author |
| 产品 | 产品 pages | name, image, offers |
| SoftwareApplication | SaaS/app pages | name, offers |
| FAQPage | FAQ content | mainEntity (Q&A array) |
| HowTo | Tutorials | name, step |
| BreadcrumbList | Any page with breadcrumbs | itemListElement |
| LocalBusiness | Local business pages | name, address |
| 事件 | Events, webinars | name, startDate, location |

**For complete JSON-LD examples**: See [references/schema-examples.md](references/schema-examples.md)

---

## 快速参考

### Organization (Company 页面)
Required: name, url
Recommended: logo, sameAs (social profiles), contactPoint

### Article/BlogPosting
Required: 标题, image, datePublished, author
Recommended: dateModified, publisher, description

### 产品
Required: name, image, offers (price + availability)
Recommended: sku, brand, aggregateRating, review

### FAQPage
Required: mainEntity (array of Question/Answer pairs)

### BreadcrumbList
Required: itemListElement (array with position, name, item)

---

## Multiple Schema Types

You can combine multiple schema types on one page using `@graph`:

```json
{
  "@context": "https://schema.org",
  "@graph": [
    { "@type": "Organization", ... },
    { "@type": "WebSite", ... },
    { "@type": "BreadcrumbList", ... }
  ]
}
```

---

## Validation and 测试

### Tools
- **Google Rich Results Test**: https://搜索.google.com/test/rich-results
- **Schema.org Validator**: https://validator.schema.org/
- **搜索 Console**: Enhancements reports

### 常见 Errors

**Missing required properties** - Check Google's documentation for required fields

**Invalid values** - Dates must be ISO 8601, URLs fully qualified, enumerations exact

**Mismatch with page content** - Schema doesn't match visible content

---

## 实现

### Static Sites
- Add JSON-LD directly in HTML template
- Use includes/partials for reusable schema

### Dynamic Sites (React, Next.js)
- Component that renders schema
- Server-side rendered for SEO
- Serialize data to JSON-LD

### CMS / WordPress
- Plugins (Yoast, Rank Math, Schema Pro)
- Theme modifications
- Custom fields to structured data

---

## 输出格式

### Schema 实现
```json
// Full JSON-LD code block
{
  "@context": "https://schema.org",
  "@type": "...",
  // Complete markup
}
```

### 测试 Checklist
- [ ] Validates in Rich Results Test
- [ ] No errors or warnings
- [ ] Matches page content
- [ ] All required properties included

---

## Task-Specific Questions

1. What 类型 of page is this?
2. What rich results are you hoping to achieve?
3. What data is available to populate the schema?
4. Is there existing schema on the page?
5. What's your tech stack?

---

## Related 技能

- **seo-audit**: For overall SEO including schema review
- **ai-seo**: For AI 搜索 optimization (schema helps AI understand content)
- **programmatic-seo**: For templated schema at scale
- **site-architecture**: For breadcrumb structure and navigation schema planning
