# Marketing 技能 版本列表

这里记录了所有 skill 的当前版本。Agent 可以将其与本地版本比较，以检查是否有更新。

| Skill | Version | Last Updated |
|-------|---------|--------------|
| ab-test-setup | 1.2.0 | 2026-03-14 |
| ad-creative | 1.2.0 | 2026-03-14 |
| ai-seo | 1.2.0 | 2026-03-14 |
| analytics-tracking | 1.2.0 | 2026-03-14 |
| churn-prevention | 1.2.0 | 2026-03-14 |
| cold-email | 1.2.0 | 2026-03-14 |
| competitor-alternatives | 1.2.0 | 2026-03-14 |
| content-strategy | 1.2.0 | 2026-03-14 |
| copy-editing | 1.2.0 | 2026-03-14 |
| copywriting | 1.2.0 | 2026-03-14 |
| email-sequence | 1.2.0 | 2026-03-14 |
| form-cro | 1.2.0 | 2026-03-14 |
| free-tool-strategy | 1.2.0 | 2026-03-14 |
| launch-strategy | 1.2.0 | 2026-03-14 |
| lead-magnets | 1.0.0 | 2026-03-14 |
| marketing-ideas | 1.2.0 | 2026-03-14 |
| marketing-psychology | 1.2.0 | 2026-03-14 |
| onboarding-cro | 1.2.0 | 2026-03-14 |
| page-cro | 1.2.0 | 2026-03-14 |
| paid-ads | 1.2.0 | 2026-03-14 |
| paywall-upgrade-cro | 1.2.0 | 2026-03-14 |
| popup-cro | 1.2.0 | 2026-03-14 |
| pricing-strategy | 1.2.0 | 2026-03-14 |
| product-marketing-context | 1.2.0 | 2026-03-14 |
| programmatic-seo | 1.2.0 | 2026-03-14 |
| referral-program | 1.2.0 | 2026-03-14 |
| revops | 1.2.0 | 2026-03-14 |
| sales-enablement | 1.2.0 | 2026-03-14 |
| schema-markup | 1.2.0 | 2026-03-14 |
| seo-audit | 1.2.0 | 2026-03-14 |
| signup-flow-cro | 1.2.0 | 2026-03-14 |
| site-architecture | 1.2.0 | 2026-03-14 |
| social-content | 1.2.0 | 2026-03-14 |

## 最近变更

### 2026-03-14
- 新增 `lead-magnets` skill，用于 lead magnet 策略、形式选择和转化优化
- 新增 Composio 集成层，为重 OAuth 工具提供 MCP 访问（HubSpot、Salesforce、Meta Ads、LinkedIn Ads、Google Sheets、Slack、Notion 等）
- 新增 headless CMS 集成指南（Sanity、Contentful、Strapi），并加入 `headless-cms` reference
- 为全部 33 个 skill 增加了 197 个 eval，用于自动化质量测试
- 优化全部 32 个既有 skill 的 description，提高触发短语匹配效果
- 把僵硬命令式写法替换成基于推理的指导方式，覆盖所有 skills
- 新增 10 个 CLI 工具（airops、clay、close、coupler、crossbeam、outreach、pendo、similarweb、supermetrics、zoominfo）
- 新增 13 份 integration guide
- 将全部 32 个既有 skill 从 1.1.0 升级到 1.2.0

### 2026-02-27
- 为了兼容不同 agent，从 `.claude/` 迁移 context 路径到 `.agents/`
- 所有 skill 现在都会优先读取 `.agents/product-marketing-context.md`，同时保留 `.claude/` 作为旧项目回退
- 更新 README 中的安装路径，统一指向 `.agents/skills/`
- 将全部 32 个 skill 从 1.0.0 升级到 1.1.0

### 2026-02-22
- 新增 `revops` skill，用于 revenue operations、线索生命周期、评分、路由、pipeline 管理和 CRM 自动化
- 新增 `sales-enablement` skill，用于销售 deck、one-pager、异议处理、demo script 和销售 playbook

### 2026-02-21
- 新增 `site-architecture` skill，用于网站结构规划、页面层级、导航设计、URL 结构和内链策略

### 2026-02-18
- 新增 `ai-seo` skill，用于 AI 搜索优化（AEO、GEO、LLMO、AI Overviews）
- 将 AEO / GEO 的内容模式从 `seo-audit` references 移到 `ai-seo`
- 新增 `churn-prevention` skill，用于取消流程、挽留优惠、催款和支付恢复

### 2026-02-17
- 新增 `ad-creative` skill，用于批量广告创意生成和基于表现的迭代
- 新增 51 个零依赖 CLI 工具，覆盖营销平台（`tools/clis/`）
- 新增 31 份 integration guide（`tools/integrations/`）
- 新增 4 个邮件外呼 CLI：hunter、snov、lemlist、instantly
- 安全加固：为 meta-ads 增加 header auth、URL 编码与输入校验
- 所有 CLI 都经过独立的 codex 审计（鉴权、安全、错误处理、一致性）

### 2026-01-27
- 首次加入版本跟踪
- 新增工具注册表，包含 29 份 integration guide
