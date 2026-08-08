# Bug Report

## Metadata
- Skill: init-project
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: ab0c189a08fb6634a3e58fd86826f17b609c4e9282659d442431a03847adaaee
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-01T14:01:59Z
- Last seen at: 2026-08-01T14:01:59Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
AGENTS 智能合并把 fenced code block 内标题误判为自定义章节

## Expected Behavior
智能合并应忽略 Markdown 代码围栏内的标题，并保留结构完整的项目指令

## Actual Behavior
现有 AGENTS 的变更记录示例含有二级标题，合并器将其提取为自定义章节并把残缺的版本示例插入新文档

## Reproduction Steps
- 在 AGENTS 的 fenced markdown 示例内包含 ## [版本号] 标题
- 运行 generate.py --auto 触发 merge_existing_file

## Evidence
- 生成结果出现游离的 ## [版本号] - YYYY-MM-DD，并只保留 Added 子段

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: workstation
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.144.0-alpha.4
  - gh: unavailable
  - git: git version 2.45.1.windows.1
  - init-project: 2.3.3
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
运行生成器后人工审查差异，移除误插入章节并按项目实际结构精修

## Additional Notes
None
