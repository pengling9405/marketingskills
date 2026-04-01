# AGENTS.md

本文件为在此仓库中工作的 AI agent 提供指南。
当前 `zh-cn-docs` 分支保留原有结构，并直接以内联方式维护中文内容。

## 仓库概览

这个仓库包含一组符合 [Agent Skills specification](https://agentskills.io/specification.md) 的 **Agent Skills**。这些 skills 安装到 `.agents/skills/`（跨 agent 的标准路径）。同时，这个仓库也通过 `.claude-plugin/marketplace.json` 充当 **Claude Code 插件市场**。

- **名称**：营销 Skills
- **GitHub**：[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills)
- **作者**：Corey Haines
- **许可证**：MIT

## 仓库结构

```
marketingskills/
├── .claude-plugin/
│   └── marketplace.json   # Claude Code 插件市场清单
├── skills/                # Agent Skills
│   └── skill-name/
│       └── SKILL.md       # 必需的 skill 文件
├── tools/
│   ├── clis/              # 零依赖 Node.js CLI 工具（51 个工具）
│   ├── composio/          # Composio 集成层（快速开始 + toolkit 映射）
│   ├── integrations/      # 每个工具对应的 API 集成指南
│   └── REGISTRY.md        # 工具索引与能力说明
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

## 构建 / Lint / 测试命令

**Skills** 只是内容文件，不需要构建步骤。手动校验即可：

- YAML frontmatter 合法
- `name` 字段与目录名完全一致
- `name` 长度为 1-64 个字符，只允许小写字母、数字和连字符
- `description` 长度为 1-1024 个字符

**CLI 工具**（`tools/clis/*.js`）是零依赖 Node.js 脚本（Node 18+）。可用下面方式校验：

```bash
node --check tools/clis/<name>.js   # 语法检查
node tools/clis/<name>.js           # 显示用法（无参数时输出帮助）
node tools/clis/<name>.js <cmd> --dry-run  # 预览请求而不真正发送
```

## Agent Skills 规范

这些 skill 遵循 [Agent Skills spec](https://agentskills.io/specification.md)。

### 必需的 Frontmatter

```yaml
---
name: skill-name
description: 这个 skill 做什么，什么时候使用。包含触发短语。
---
```

### Frontmatter 字段约束

| 字段 | 必填 | 约束 |
|---------------|----------|------------------------------------------------------------------|
| `name` | 是 | 1-64 个字符，只允许小写 `a-z`、数字和连字符。必须与目录名一致。 |
| `description` | 是 | 1-1024 个字符。要说明它做什么、何时使用。 |
| `license` | 否 | 许可证名称（默认：MIT） |
| `metadata` | 否 | 键值对（author、version 等） |

### `name` 字段规则

- 只能使用小写字母、数字和连字符
- 不能以连字符开头或结尾
- 不能出现连续连字符（`--`）
- 必须与父目录名完全一致

**有效**：`page-cro`、`email-sequence`、`ab-test-setup`  
**无效**：`Page-CRO`、`-page`、`page--cro`

### 可选的 Skill 目录结构

```
skills/skill-name/
├── SKILL.md        # 必需 - 主说明文件（<500 行）
├── references/     # 可选 - 按需加载的详细文档
├── scripts/        # 可选 - 可执行代码
└── assets/         # 可选 - 模板、数据文件
```

## 写作风格指南

### 结构

- `SKILL.md` 控制在 500 行以内（细节移到 `references/`）
- 主章节使用 H2（`##`），子章节使用 H3（`###`）
- 多用项目符号和编号列表
- 段落保持简短（最多 2-4 句）

### 语气

- 直接、指导性强
- 使用第二人称（例如“你是一位转化率优化专家”）
- 专业，但不要生硬

### 格式

- 关键术语用粗体（`**text**`）
- 示例和模板用代码块
- 参考数据用表格
- 不要滥用 emoji

### 清晰度原则

- 清晰优先于炫技
- 具体优先于模糊
- 主动语态优先于被动语态
- 每个章节只讲一个核心点

### `description` 字段最佳实践

`description` 对 skill 发现非常关键。应包含：

1. 这个 skill 做什么
2. 什么时候使用（触发短语）
3. 相关 skill，用于划定边界

```yaml
description: 当用户希望优化任意营销页面的转化时使用。适用于用户说 “CRO”、“conversion rate optimization” 或 “this page isn't converting” 之类情况。对于 signup 流程，请看 signup-flow-cro。
```

## Claude Code 插件

本仓库同时也作为插件市场使用。`.claude-plugin/marketplace.json` 会列出所有 skill，可通过以下命令安装：

```bash
/plugin marketplace add coreyhaines31/marketingskills
/plugin install marketing-skills
```

详情见 [Claude Code plugins documentation](https://code.claude.com/docs/en/plugins.md)。

## Git 工作流

### 分支命名

- 新 skill：`feature/skill-name`
- 改进：`fix/skill-name-description`
- 文档：`docs/description`

### Commit Message

遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范：

- `feat: add skill-name skill`
- `fix: improve clarity in page-cro`
- `docs: update README`

### Pull Request 检查清单

- [ ] `name` 与目录名完全一致
- [ ] `name` 符合命名规则（小写、连字符、无 `--`）
- [ ] `description` 长度 1-1024 字符，并包含触发短语
- [ ] `SKILL.md` 少于 500 行
- [ ] 不包含敏感数据或凭据

## 工具集成

这个仓库还包含了一个面向 agent 的营销工具注册表。

- **工具发现**：读取 `tools/REGISTRY.md` 查看可用工具及其能力
- **集成细节**：查看 `tools/integrations/{tool}.md` 获取 API、鉴权和常见操作说明
- **支持 MCP 的工具**：ga4、stripe、mailchimp、google-ads、resend、zapier、zoominfo、clay、supermetrics、coupler、outreach、crossbeam、introw、composio
- **Composio**（集成层）：为没有原生 MCP server 的重 OAuth 工具提供 MCP 接入（例如 HubSpot、Salesforce、Meta Ads、LinkedIn Ads、Google Sheets、Slack 等）。见 `tools/integrations/composio.md`

### 注册表结构

```
tools/
├── REGISTRY.md              # 所有工具及能力的索引
└── integrations/            # 详细集成指南
    ├── ga4.md
    ├── stripe.md
    ├── rewardful.md
    └── ...
```

### 什么时候使用这些工具

各个 skill 会引用相关工具进行实现。例如：

- `referral-program` skill → rewardful、tolt、dub-co、mention-me 指南
- `analytics-tracking` skill → ga4、mixpanel、segment 指南
- `email-sequence` skill → 客户-io、mailchimp、resend 指南
- `paid-ads` skill → google-ads、meta-ads、linkedin-ads 指南

对于没有原生 MCP server 的工具（HubSpot、Salesforce、Meta Ads、LinkedIn Ads、Google Sheets、Slack、Notion），可以通过 Composio 用单个 server 提供 MCP 接入。配置见 `tools/integrations/composio.md`，完整映射见 `tools/composio/marketing-tools.md`。

## 检查更新

在使用本仓库任何 skill 时：

1. **每个会话只检查一次**，在首次使用 skill 时执行：
   - 从 GitHub 拉取 `VERSIONS.md`：<https://raw.githubusercontent.com/coreyhaines31/marketingskills/main/VERSIONS.md>
   - 将远程版本与本地 skill 文件版本对比

2. **只有在有意义时才提示用户**：
   - 2 个及以上 skill 有更新，或者
   - 任意 skill 出现 major version 升级（例如 1.x → 2.x）

3. **非阻塞提示**，放在回答末尾：
   ```
   ---
   Skills 有更新：有 X 个营销 skill 存在新版本。
   你可以直接说“update skills”让它自动更新，或者在 marketingskills 目录里运行 `git pull`。
   ```

4. **如果用户说 “update skills”**：
   - 在 marketingskills 目录里运行 `git pull`
   - 告知用户具体更新了什么

## Skill 分类

当前 skill 列表按分类组织，详见 `README.md`。新增 skill 时，遵循该分类中已有 skill 的命名模式。

## Claude Code 专属增强

以下模式**仅适用于 Claude Code**，不应直接加入 `SKILL.md` 文件，因为这些 skill 设计上要兼容不同 agent（Codex、Cursor、Windsurf 等）。如果需要，请在你自己的项目 `.claude/skills/` 覆盖层中本地应用这些增强。

### 通过 `` !`command` `` 动态注入内容

Claude Code 支持在 SKILL.md 里嵌入 shell 命令，语法是 `` !`command` ``。当 skill 被调用时，Claude Code 会执行命令并把结果直接注入上下文，也就是说模型看到的是结果，不是命令说明。

**最有价值的用途：自动注入 product marketing context 文件**

与其让每个 skill 都写“先检查 `.agents/产品-营销-context.md` 是否存在，再去读取它”，不如直接自动注入：

```markdown
Product context: !`cat .agents/product-marketing-context.md 2>/dev/null || echo "No product context file found — ask the user about their product before proceeding."`
```

把这段放在 skill 正文顶部（frontmatter 后）即可。这样上下文在一开始就可用，不再需要额外的读文件步骤。
