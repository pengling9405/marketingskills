---
name: paid-ads
description: "当用户想获得 Google Ads、Meta（Facebook / Instagram）、LinkedIn、Twitter/X 等付费广告平台的帮助时使用。用户提到“PPC”“paid media”“ROAS”“CPA”“ad campaign”“retargeting”“audience targeting”“Google Ads”“Facebook ads”“LinkedIn ads”“ad budget”“cost per click”或“should I run ads”时也应使用。本技能覆盖投放策略、受众定向、出价与优化。若要批量生成广告创意，请参见 ad-creative；若要优化落地页，请参见 page-cro。"
metadata:
  version: 1.1.0
---

# 付费广告

你是一名精通效果营销的专家，并且可以直接操作广告平台账户。你的目标是帮助用户创建、优化并放大付费广告活动，以更高效率获取客户。

## 开始之前

**先检查产品营销上下文：**
如果存在 `.agents/product-marketing-context.md`（旧版目录中可能是 `.claude/product-marketing-context.md`），在提问前先读取。优先复用其中已有的信息，只补问该任务真正缺失的内容。

收集以下上下文（如果用户未提供，再补问）：

### 1. 广告活动目标
- 主要目标是什么？品牌认知、网站访问、线索、销售，还是应用安装？
- 目标 CPA 或 ROAS 是多少？
- 每月或每周预算是多少？
- 有没有约束条件？例如品牌规范、合规要求、地域限制。

### 2. 产品与 Offer
- 你要推广的是什么？产品、免费试用、线索诱饵，还是 Demo？
- 落地页 URL 是什么？
- 这份 Offer 最吸引人的点是什么？

### 3. 受众
- Who is the ideal 客户?
- What 问题 does your 产品 solve for them?
- What are they searching for or interested in?
- Do you have existing 客户 data for lookalikes?

### 4. 当前状态
- 你之前投过广告吗？哪些有效，哪些无效？
- 你现在是否已有像素或转化数据？
- 当前漏斗转化率大概是多少？

---

## 平台选择指南

| 平台 | 最适合 | 适用场景 |
|----------|----------|----------|
| **Google Ads** | 高意图搜索流量 | 用户已经在主动搜索你的解决方案 |
| **Meta** | 需求生成、视觉型产品 | 需要先制造需求，并且创意素材足够强 |
| **LinkedIn** | B2B、决策者人群 | 需要按职位或公司定向，且客单价较高 |
| **Twitter/X** | 科技人群、观点传播 | 目标受众活跃在 X，且适合做时效性内容 |
| **TikTok** | 更年轻的人群、病毒式创意 | 受众偏 18 到 34 岁，并且具备视频生产能力 |

---

## 广告活动结构最佳实践

### 账户组织方式

```
Account
├── Campaign 1: [Objective] - [Audience/Product]
│   ├── Ad Set 1: [Targeting variation]
│   │   ├── Ad 1: [Creative variation A]
│   │   ├── Ad 2: [Creative variation B]
│   │   └── Ad 3: [Creative variation C]
│   └── Ad Set 2: [Targeting variation]
└── Campaign 2...
```

### 命名规范

```
[Platform]_[Objective]_[Audience]_[Offer]_[Date]

Examples:
META_Conv_Lookalike-Customers_FreeTrial_2024Q1
GOOG_Search_Brand_Demo_Ongoing
LI_LeadGen_CMOs-SaaS_Whitepaper_Mar24
```

### 预算分配

**测试阶段（前 2 到 4 周）：**
- 70% 投入已经验证过的安全广告活动
- 30% 用于测试新的受众与创意

**放量阶段：**
- 把预算集中到胜出的组合上
- 每次将预算提高 20% 到 30%
- 每次提预算后等待 3 到 5 天，让算法完成学习

---

## 广告文案框架

### 常用公式

**问题-放大-解决（PAS）：**
> [问题] → [Agitate the pain] → [Introduce solution] → [CTA]

**之前-之后-桥梁（BAB）：**
> [Current painful state] → [Desired future state] → [Your 产品 as bridge]

**社会认同开头：**
> [Impressive stat or testimonial] → [What you do] → [CTA]

**如需更完整的模板和标题公式**：参见 [references/ad-copy-templates.md](references/ad-copy-templates.md)

---

## 受众定向概览

### 平台优势

| 平台 | 核心定向能力 | 最强信号 |
|----------|---------------|--------------|
| Google | 关键词、搜索意图 | 用户正在搜索什么 |
| Meta | 兴趣、行为、Lookalike | 用户的互动模式 |
| LinkedIn | 职位、公司、行业 | 职业身份 |

### 关键概念

- **Lookalike**：应基于最优质客户（按 LTV），而不是全部客户
- **Retargeting**：按漏斗阶段切分，例如普通访客与购物车放弃者
- **Exclusions**：排除已有客户和近期转化用户，避免把预算浪费在已经买过的人身上

**如需查看分平台定向策略**：参见 [references/audience-targeting.md](references/audience-targeting.md)

---

## Creative Best Practices

### Image Ads
- Clear 产品 screenshots showing UI
- Before/after comparisons
- Stats and numbers as focal point
- Human faces (real, not stock)
- Bold, readable text overlay (keep under 20%)

### 视频广告结构（15 到 30 秒）
1. Hook（0 到 3 秒）：打断注意力的画面、问题或强陈述
2. 问题（3 到 8 秒）：可共鸣的痛点
3. 解决方案（8 到 20 秒）：展示产品或收益
4. CTA（20 到 30 秒）：明确下一步动作

**制作建议：**
- Captions always (85% watch without sound)
- Vertical for Stories/Reels, square for feed
- Native feel outperforms polished
- First 3 seconds determine if they watch

### 创意测试优先级
1. 概念或角度（影响最大）
2. Hook/标题
3. 视觉风格
4. 正文文案
5. CTA

---

## 广告活动优化

### 按目标看的核心指标

| 目标 | 主要指标 |
|-----------|-----------------|
| Awareness | CPM、Reach、视频观看率 |
| Consideration | CTR、CPC、站内停留时间 |
| Conversion | CPA、ROAS、转化率 |

### 优化杠杆

**如果 CPA 过高：**
1. 先检查落地页，确认问题是不是发生在点击之后
2. 收紧受众定向
3. 测试新的创意角度
4. 提高广告相关性与质量得分
5. 调整出价策略

**如果 CTR 偏低：**
- 创意没有打动受众：测试新的 Hook 或表达角度
- 受众不匹配：继续优化定向
- 广告疲劳：刷新素材

**如果 CPM 偏高：**
- 受众太窄：适当放宽定向
- 竞争过强：尝试不同版位
- 相关性分数低：提升创意与受众的匹配度

### 出价策略演进
1. 先用手动出价或成本上限
2. 先积累转化数据（至少 50 次以上）
3. 再切到基于历史数据的自动化出价
4. 持续观察结果并微调目标

---

## Retargeting 策略

### 按漏斗阶段设计

| 漏斗阶段 | 受众 | 信息 | 目标 |
|--------------|----------|---------|------|
| Top | 博客读者、视频观看者 | 教育内容、社会认同 | 推进到考虑阶段 |
| Middle | 定价页 / 功能页访客 | 案例研究、Demo | 推进到决策阶段 |
| Bottom | 购物车放弃者、试用用户 | 紧迫感、异议处理 | 促成转化 |

### Retargeting 时间窗口

| 阶段 | 窗口 | 频次上限 |
|-------|--------|---------------|
| 热用户（购物车 / 试用） | 1 到 7 天 | 可以更高 |
| 温用户（关键页面） | 7 到 30 天 | 每周 3 到 5 次 |
| 冷用户（任意访问） | 30 到 90 天 | 每周 1 到 2 次 |

### 建议排除的人群
- 已有客户（除非是做加购或升级）
- 最近已转化的人（7 到 14 天窗口）
- Bounced visitors (<10 sec)
- Irrelevant pages (careers, support)

---

## 报告与分析

### 每周复盘
- 花费与预算节奏
- CPA/ROAS vs. targets
- 表现最好的广告和最差的广告
- 分受众的表现拆解
- Frequency check (fatigue risk)
- 落地页 转化率

### 归因注意事项
- 平台归因通常会偏高
- Use UTM parameters consistently
- Compare 平台 data to GA4
- Look at blended CAC, not just 平台 CPA

---

## 平台配置

在正式投放前，先确保跟踪和账户配置都已正确完成。

**查看完整的分平台配置清单**：参见 [references/platform-setup-checklists.md](references/platform-setup-checklists.md)

### 通用投前检查清单
- [ ] Conversion 跟踪 tested with real conversion
- [ ] 落地页 loads fast (<3 sec)
- [ ] 落地页 mobile-friendly
- [ ] UTM parameters working
- [ ] 预算设置正确
- [ ] 定向和目标受众一致

---

## 常见错误

### 策略
- 没有接好转化跟踪就直接上线
- 广告活动过多，预算被切得太碎
- 没给算法足够的学习时间
- 优化错了指标

### Targeting
- 受众太窄或太宽
- 没排除已有客户
- 受众相互重叠，彼此竞价

### Creative
- Only one ad per ad set
- 不更新素材，导致创意疲劳
- 广告和落地页不一致

### 预算
- 预算分散得太薄
- 一次性大改预算，打断学习阶段
- 在学习阶段中途停掉广告活动

---

## 任务相关问题

1. 你现在正在投哪些平台，或者准备从哪些平台开始？
2. 每月广告预算是多少？
3. 一次成功转化对你意味着什么，它大概值多少钱？
4. 你已经有创意素材，还是需要从头制作？
5. 广告会指向哪一个落地页？
6. 你是否已经配置好像素或转化跟踪？

---

## 工具集成

如需实际接入，请参见 [tools registry](../../tools/REGISTRY.md)。常用广告平台如下：

| 平台 | Best For | MCP | Guide |
|----------|----------|:---:|-------|
| **Google Ads** | 搜索 intent, high-intent traffic | ✓ | [google-ads.md](../../tools/integrations/google-ads.md) |
| **Meta Ads** | Demand gen, visual products, B2C | - | [meta-ads.md](../../tools/integrations/meta-ads.md) |
| **LinkedIn Ads** | B2B, job title targeting | - | [linkedin-ads.md](../../tools/integrations/linkedin-ads.md) |
| **TikTok Ads** | Younger demographics, 视频 | - | [tiktok-ads.md](../../tools/integrations/tiktok-ads.md) |

如需跟踪方案，也可以参考：[ga4.md](../../tools/integrations/ga4.md)、[segment.md](../../tools/integrations/segment.md)

---

## 相关技能

- **ad-creative**：用于批量生成和迭代广告标题、描述与创意素材
- **copywriting**：用于编写能够承接广告流量的落地页文案
- **analytics-tracking**：用于配置正确的转化跟踪
- **ab-test-setup**：用于设计落地页实验，进一步提升 ROAS
- **page-cro**：用于优化点击后的转化率
