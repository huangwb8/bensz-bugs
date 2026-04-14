# Bug Report

## Metadata
- Skill: compact-bensz-skills
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: e176df4897c34c4e37e46539d5aa3bed291f479ecfecc6a3955209627e264d7b
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-04-11T00:45:09Z
- Last seen at: 2026-04-11T00:45:09Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
validate_compaction 在连续 measure/validate 场景下存在不稳定读取与 frontmatter.description 假阳性

## Expected Behavior
在同一 run 中重跑 measure_markdown.py 后，validate_compaction.py 应稳定读取 size-after.json，并且当 SKILL.md frontmatter.description 与快照解析结果相同的时候不应继续给出 warning。

## Actual Behavior
一次连续执行中，validate_compaction.py 报出 JSONDecodeError，提示无法解析 size-after.json；随后在 description 解析结果已与快照完全一致时，validation.json 仍保留 description changed warning。

## Reproduction Steps
- 对目标 skill 运行 init_workspace.py 建立 run 目录。
- 修改 SKILL.md 后，运行 measure_markdown.py --phase after。
- 紧接着运行 validate_compaction.py；一次执行出现 JSONDecodeError。
- 将 frontmatter.description 恢复为与快照完全相同后再次运行 validate_compaction.py；warning 仍未消失。

## Evidence
- JSONDecodeError: Expecting value: line 1 column 1 (char 0)
- 使用 common.parse_frontmatter 对当前 SKILL.md 与快照的 description 做比较，结果为 True，但 validation.json 仍报告 description changed warning。

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.4.0 / arm64
- Shell: /bin/zsh
- Agent runtime: OpenAI Codex CLI
- Key software versions:
  - claude: 2.1.92 (Claude Code)
  - codex: codex-cli 0.118.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python: 3.12
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
重跑 validate_compaction.py 后可继续完成任务；description warning 需要人工确认为工具级假阳性，不影响本次压缩结果。

## Additional Notes
None
