# bensz-bugs

用于公开收集与管理 Bensz 系列 Agent Skills 在真实用户环境中暴露出的设计缺陷类 bug。

## 仓库约定

每个 bug 目录使用以下层级：

```text
{skill_name}/{github_username}/{bug_hash}/
```

其中：
- `skill_name`：出问题的 skill 名称
- `github_username`：报告者的 GitHub 用户名（优先来自 `gh auth status`）
- `bug_hash`：基于规范化 bug 指纹计算出的稳定哈希，用于避免重复上传同一问题

## 每个 bug 目录必须包含的文件

- `bug-context.json`
  - 记录运行环境、工具版本、报告者、skill 作者、采集时间、去重状态等结构化信息
- `BUG_REPORT.md`
  - 记录 bug 现象、复现步骤、预期行为、实际行为、影响范围、证据和后续补充

## 哈希建议

建议对以下信息做 JSON 规范化后计算 `sha256`：
- `skill_name`
- `skill_author`
- `reporter_identity`
- `bug_summary`
- `expected_behavior`
- `actual_behavior`
- `reproduction_steps`
- `environment_fingerprint`

## 上传约束

- 不要求拉取整个仓库。
- 推荐通过 `gh api repos/{owner}/{repo}/contents/{path}` 直接创建文件。
- 若远端已存在同一路径，则视为该 bug 已公开，不重复上传。
