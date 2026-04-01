# 面向 AI 代理的营销技能

这是一个聚焦营销任务的 AI 代理技能集合。它面向技术型营销人和创始人，帮助 AI 编码代理处理转化优化、文案撰写、SEO、数据分析和增长工程等工作。可用于 Claude Code、OpenAI Codex、Cursor、Windsurf，以及任何支持 [Agent Skills spec](https://agentskills.io) 的代理。

由 [Corey Haines](https://corey.co?ref=marketingskills) 构建。想要落地执行支持？可以了解 [Conversion Factory](https://conversionfactory.co?ref=marketingskills)，这是 Corey 的转化优化、落地页和增长策略咨询机构。想学更多营销？可以订阅 [Swipe Files](https://swipefiles.com?ref=marketingskills)。如果你想要一个能使用这些 skill、像 CMO 一样工作的自治 AI agent，可以看看 [Magister](https://magistermarketing.com?ref=marketingskills)。

如果你刚开始接触终端和编码代理，可以看看配套指南 [Coding for Marketers](https://codingformarketers.com?ref=marketingskills)。

**欢迎贡献！** 如果你找到改进某个 skill 的方式，或者有新的 skill 想法，可以[提交 PR](#contributing)。

如果你遇到问题或有疑问，可以[提交 issue](https://github.com/coreyhaines31/marketingskills/issues)，我们很乐意帮忙。

## 什么是技能？

技能是 Markdown 文件，用来给 AI 代理提供某一类任务的专业知识和工作流。当你把这些文件加入项目后，代理就能识别你当前是否在处理营销任务，并自动套用合适的框架与最佳实践。

## 技能如何协同工作

各个技能会互相引用，并建立在共享上下文之上。`product-marketing-context` 是基础层，其他所有技能在真正开始工作前，都会先读取它，理解你的产品、受众和定位。

```
                            ┌──────────────────────────────────────┐
                            │      product-marketing-context       │
                            │    (read by all other skills first)  │
                            └──────────────────┬───────────────────┘
                                               │
    ┌──────────────┬─────────────┬─────────────┼─────────────┬──────────────┬──────────────┐
    ▼              ▼             ▼             ▼             ▼              ▼              ▼
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────────┐ ┌──────────┐ ┌─────────────┐ ┌───────────┐
│  SEO &   │ │   CRO    │ │Content & │ │  Paid &    │ │ Growth & │ │  Sales &    │ │ Strategy  │
│ Content  │ │          │ │   Copy   │ │Measurement │ │Retention │ │    GTM      │ │           │
├──────────┤ ├──────────┤ ├──────────┤ ├────────────┤ ├──────────┤ ├─────────────┤ ├───────────┤
│seo-audit │ │page-cro  │ │copywritng│ │paid-ads    │ │referral  │ │revops       │ │mktg-ideas │
│ai-seo    │ │signup-cro│ │copy-edit │ │ad-creative │ │free-tool │ │sales-enable │ │mktg-psych │
│site-arch │ │onboard   │ │cold-email│ │ab-test     │ │churn-    │ │launch       │ │customer-  │
│programm  │ │form-cro  │ │email-seq │ │analytics   │ │ prevent  │ │pricing      │ │research   │
│schema    │ │popup-cro │ │social    │ │            │ │          │ │competitor   │ │           │
│content   │ │paywall   │ │          │ │            │ │          │ │             │ │           │
└────┬─────┘ └────┬─────┘ └────┬─────┘ └─────┬──────┘ └────┬─────┘ └──────┬──────┘ └─────┬─────┘
     │            │            │              │             │              │              │
     └────────────┴─────┬──────┴──────────────┴─────────────┴──────────────┴──────────────┘
                        │
         Skills cross-reference each other:
           copywriting ↔ page-cro ↔ ab-test-setup
           revops ↔ sales-enablement ↔ cold-email
           seo-audit ↔ schema-markup ↔ ai-seo
           customer-research → copywriting, page-cro, competitor-alternatives
```

完整依赖关系见各个 skill 中的 **Related Skills** 章节。

## 可用技能

<!-- SKILLS:START -->
| Skill | Description |
|-------|-------------|
| [ab-test-setup](skills/ab-test-setup/) | 当用户希望规划、设计或实施 A/B 测试 / 实验时使用。也适用于用户提到 “A/B... |
| [ad-creative](skills/ad-creative/) | 当用户希望生成、迭代或批量扩展广告创意时使用，包括标题、描述、主文案或完整广告... |
| [ai-seo](skills/ai-seo/) | 当用户希望为 AI 搜索引擎优化内容、在 LLM 结果中被引用，或出现在 AI 生成回答中时使用.... |
| [analytics-tracking](skills/analytics-tracking/) | 当用户希望搭建、改进或审计数据追踪与测量时使用。也适用于用户提到... |
| [churn-prevention](skills/churn-prevention/) | 当用户希望降低流失、设计取消流程、设置挽留优惠、恢复失败付款或... |
| [cold-email](skills/cold-email/) | 撰写能获得回复的 B2B 冷邮件和跟进序列。适用于用户需要写外呼邮件... |
| [competitor-alternatives](skills/competitor-alternatives/) | 当用户希望为 SEO 或销售赋能创建竞品对比页 / alternative 页时使用。也适用于... |
| [content-strategy](skills/content-strategy/) | 当用户希望规划内容策略、决定写什么内容或梳理主题时使用。也适用于... |
| [copy-editing](skills/copy-editing/) | 当用户希望编辑、审阅或改进现有营销文案时使用。也适用于用户说 “edit this... |
| [copywriting](skills/copywriting/) | 当用户希望撰写、重写或优化任意页面的营销文案时使用，包括首页、落地页... |
| [customer-research](skills/customer-research/) | 当用户希望开展、分析或综合客户研究时使用，包括访谈稿、问卷、工单、评论挖掘、Reddit/G2/论坛研究、persona 生成和 VOC... |
| [email-sequence](skills/email-sequence/) | 当用户希望创建或优化邮件序列、drip campaign、自动化邮件流或生命周期邮件时使用... |
| [form-cro](skills/form-cro/) | 当用户希望优化任何非注册类表单时使用，包括获客表单、联系表单... |
| [free-tool-strategy](skills/free-tool-strategy/) | 当用户希望规划、评估或构建用于营销目的的免费工具时使用，例如获客、SEO 价值或... |
| [launch-strategy](skills/launch-strategy/) | 当用户希望规划产品发布、功能公告或 release strategy 时使用。也适用于用户... |
| [lead-magnets](skills/lead-magnets/) | 当用户希望创建、规划或优化用于邮箱收集 / lead generation 的 lead magnet 时使用。也适用于... |
| [marketing-ideas](skills/marketing-ideas/) | 当用户需要营销创意、灵感或 SaaS / 软件产品营销策略时使用。也适用于... |
| [marketing-psychology](skills/marketing-psychology/) | 当用户希望把心理学原则、心智模型或行为科学应用到营销中时使用。也适用于... |
| [onboarding-cro](skills/onboarding-cro/) | 当用户希望优化注册后的 onboarding、用户激活、首次使用体验或价值到达时间时使用... |
| [page-cro](skills/page-cro/) | 当用户希望优化、改进或提升任意营销页面的转化时使用，包括首页、落地页... |
| [paid-ads](skills/paid-ads/) | 当用户需要 Google Ads、Meta、LinkedIn、Twitter/X 等付费广告投放支持时使用... |
| [paywall-upgrade-cro](skills/paywall-upgrade-cro/) | 当用户希望创建或优化产品内 paywall、升级页、upsell 弹窗或 feature gate 时使用... |
| [popup-cro](skills/popup-cro/) | 当用户希望创建或优化弹窗、模态框、overlay、slide-in 或 banner 以提升转化时使用... |
| [pricing-strategy](skills/pricing-strategy/) | 当用户希望获得定价决策、套餐设计或变现策略支持时使用。也适用于用户提到... |
| [product-marketing-context](skills/product-marketing-context/) | 当用户希望创建或更新产品营销上下文文档时使用。也适用于用户提到... |
| [programmatic-seo](skills/programmatic-seo/) | 当用户希望通过模板和数据批量生成 SEO 页面时使用。也适用于用户提到... |
| [referral-program](skills/referral-program/) | 当用户希望创建、优化或分析 referral program、affiliate program 或口碑传播策略时使用... |
| [revops](skills/revops/) | 当用户需要 revenue operations、线索生命周期管理或营销到销售交接流程支持时使用... |
| [sales-enablement](skills/sales-enablement/) | 当用户希望创建销售资料、pitch deck、one-pager、异议处理文档或 demo script 时使用... |
| [schema-markup](skills/schema-markup/) | 当用户希望在网站上新增、修复或优化 schema markup 与结构化数据时使用。也适用于... |
| [seo-audit](skills/seo-audit/) | 当用户希望审计、检查或诊断站点 SEO 问题时使用。也适用于用户提到 “SEO... |
| [signup-flow-cro](skills/signup-flow-cro/) | 当用户希望优化注册、账户创建或 trial 激活流程时使用。也适用于用户... |
| [site-architecture](skills/site-architecture/) | 当用户希望规划、梳理或重构网站页面层级、导航、URL 结构或内链时使用... |
| [social-content](skills/social-content/) | 当用户希望创建、排期或优化 LinkedIn、Twitter/X、Instagram 等平台的社媒内容时使用... |
<!-- SKILLS:END -->

## 安装方式

### 选项 1：CLI 安装（推荐）

使用 [npx skills](https://github.com/vercel-labs/skills) 直接安装：

```bash
# 安装全部技能
npx skills add coreyhaines31/marketingskills

# 安装指定技能
npx skills add coreyhaines31/marketingskills --skill page-cro copywriting

# 列出可用技能
npx skills add coreyhaines31/marketingskills --list
```

这会自动安装到你的 `.agents/skills/` 目录（并为 Claude Code 兼容性同步创建 `.claude/skills/` 的 symlink）。

### 选项 2：Claude Code 插件

通过 Claude Code 内置插件系统安装：

```bash
# 添加 marketplace
/plugin marketplace add coreyhaines31/marketingskills

# 安装全部营销技能
/plugin install marketing-skills
```

### 选项 3：Clone 后复制

克隆整个仓库，然后复制 `skills` 目录：

```bash
git clone https://github.com/coreyhaines31/marketingskills.git
cp -r marketingskills/skills/* .agents/skills/
```

### 选项 4：Git Submodule

用 submodule 方式添加，方便后续更新：

```bash
git submodule add https://github.com/coreyhaines31/marketingskills.git .agents/marketingskills
```

然后从 `.agents/marketingskills/skills/` 引用各 skill。

### 选项 5：Fork 并定制

1. Fork 本仓库
2. 按你的需求定制这些 skills
3. 把你的 fork clone 到项目中

### 选项 6：SkillKit（多 Agent）

使用 [SkillKit](https://github.com/rohitg00/skillkit) 在多个 AI agent（Claude Code、Cursor、Copilot 等）之间安装：

```bash
# 安装全部 技能
npx skillkit install coreyhaines31/marketingskills

# 安装指定 技能
npx skillkit install coreyhaines31/marketingskills --skill page-cro copywriting

# 列出可用 技能
npx skillkit install coreyhaines31/marketingskills --list
```

## 从 v1.0 升级

这些 skill 现在使用 `.agents/` 而不是 `.claude/` 来存放 产品营销上下文 文件。把现有上下文文件迁移过来：

```bash
mkdir -p .agents
mv .claude/product-marketing-context.md .agents/product-marketing-context.md
```

这些 skill 仍然会把 `.claude/` 作为回退路径检查，所以即使你不迁移，也不会直接坏掉。

## 使用方式

安装完成后，直接让 agent 帮你处理营销任务即可：

```
"Help me optimize this 落地页 for conversions"
→ 使用 page-cro skill

"Write 首页 copy for my SaaS"
→ 使用 copywriting skill

"Set up GA4 tracking for signups"
→ 使用 analytics-tracking skill

"Create a 5-email welcome sequence"
→ 使用 email-sequence skill
```

你也可以直接调用 skill：

```
/page-cro
/email-sequence
/seo-audit
```

## 技能 分类

### 转化优化
- `page-cro` - 任意营销页面
- `signup-flow-cro` - 注册流程
- `onboarding-cro` - 注册后激活
- `form-cro` - 获客表单
- `popup-cro` - 弹窗与 overlay
- `paywall-upgrade-cro` - 产品内升级时刻

### 内容与文案
- `copywriting` - 营销页面文案
- `copy-editing` - 编辑与润色现有文案
- `cold-email` - B2B 冷启动外呼邮件与序列
- `email-sequence` - 自动化邮件流
- `social-content` - 社交媒体内容

### SEO 与内容发现
- `seo-audit` - 技术 SEO 与 on-page SEO
- `ai-seo` - AI 搜索优化（AEO、GEO、LLMO）
- `programmatic-seo` - 批量页面生成
- `site-architecture` - 页面层级、导航与 URL 结构
- `competitor-alternatives` - 对比页与 alternative 页
- `schema-markup` - 结构化数据

### 付费投放与分发
- `paid-ads` - Google、Meta、LinkedIn 广告投放
- `ad-creative` - 批量广告创意生成与迭代
- `social-content` - 社媒排期与策略

### 测量与测试
- `analytics-tracking` - 事件追踪搭建
- `ab-test-setup` - 实验设计

### 留存
- `churn-prevention` - 取消流程、挽留优惠、催款与支付恢复

### 增长工程
- `free-tool-strategy` - 免费工具与计算器策略
- `referral-program` - 推荐与联盟计划

### 策略与变现
- `marketing-ideas` - 140 个 SaaS 营销想法
- `marketing-psychology` - 心智模型与营销心理学
- `launch-strategy` - 产品发布与公告
- `pricing-strategy` - 定价、套餐与变现

### 销售与 RevOps
- `revops` - 线索生命周期、评分、路由和 pipeline 管理
- `sales-enablement` - 销售 deck、one-pager、异议处理文档、demo script

## 贡献

如果你知道如何改进某个 skill，或者有新的 skill 想法，欢迎提 PR 和 issue。

新增或优化 skill 的详细规范见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 许可证

[MIT](LICENSE) - 想怎么用都可以。
