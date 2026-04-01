# 贡献指南

感谢你有兴趣为 Marketing Skills 做贡献。本指南会帮助你新增 skill 或改进现有 skill。

## 提出 技能 请求

你也可以通过[提交 skill request](https://github.com/coreyhaines31/marketingskills/issues/new?template=skill-request.yml)来建议新增 skill。

## 新增一个 技能

### 1. 创建 技能 目录

```bash
mkdir -p skills/your-skill-name
```

### 2. 创建 `SKILL.md` 文件

每个 skill 都需要一个带 YAML frontmatter 的 `SKILL.md` 文件：

```yaml
---
name: your-skill-name
description: 说明这个 skill 什么时候用。包含触发短语和关键词，帮助 agent 识别相关任务。
---

# Your 技能 Name

Instructions for the agent go here...
```

可选 frontmatter 字段：`license`（默认 MIT）、`metadata`（author、version 等）。

### 3. 遵循命名规范

- **目录名**：小写，仅使用连字符（例如 `email-sequence`）
- **name 字段**：必须与目录名完全一致
- **description**：1-1024 个字符，并包含触发短语

### 4. 组织你的 技能

```
skills/your-skill-name/
├── SKILL.md           # 必需 - 主说明文件
├── references/        # 可选 - 补充文档
│   └── guide.md
├── scripts/           # 可选 - 可执行代码
│   └── helper.py
└── assets/            # 可选 - 模板、图片、数据
    └── template.json
```

### 5. 写出有效说明

- 把 `SKILL.md` 控制在 500 行以内
- 详细参考资料移到 `references/`
- 提供逐步说明
- 加入输入 / 输出示例
- 覆盖常见边界情况

## 改进现有 技能

1. 彻底读懂现有 skill
2. 在本地测试你的改动
3. 保持改动聚焦且最小
4. 如果改动较大，在 metadata 里更新版本号

## 提交你的贡献

1. Fork 这个仓库
2. 创建功能分支（`git checkout -b feature/new-skill-name`）
3. 进行修改
4. 用 AI agent 在本地测试
5. 使用合适的模板提交 pull request：
   - [New Skill](?template=new-skill.md)
   - [Skill Update](?template=skill-update.md)
   - [Documentation](?template=documentation.md)

## 技能 质量检查清单

- [ ] `name` 与目录名一致
- [ ] `description` 清楚说明何时使用该 skill
- [ ] 说明清晰且可执行
- [ ] 不包含敏感数据或凭据
- [ ] 遵循仓库中现有 skill 的模式

## 有问题？

如果你有疑问，或在贡献过程中需要帮助，请提交 issue。
