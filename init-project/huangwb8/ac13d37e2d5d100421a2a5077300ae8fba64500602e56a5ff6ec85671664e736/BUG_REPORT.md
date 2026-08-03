# Bug Report

## Metadata
- Skill: init-project
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: ac13d37e2d5d100421a2a5077300ae8fba64500602e56a5ff6ec85671664e736
- Severity: high
- Occurrence count: 1
- First seen at: 2026-08-03T14:55:52Z
- Last seen at: 2026-08-03T14:55:52Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
智能合并把三级标题误判为二级章节并截断项目自定义规则

## Expected Behavior
智能合并应完整保留项目目标、核心工作流及自定义章节中的所有三级标题和正文，只更新标准章节。

## Actual Behavior
合并器用于识别二级章节的正则也匹配三级标题，导致核心工作流、自定义章节中的三级标题及后续正文被截断；自动生成的项目用途句还可能出现重复标点。

## Reproduction Steps
- 在已有 AGENTS.md 的核心工作流中加入三级标题和多段规则。
- 运行 init-project generate.py --auto 触发智能合并。
- 检查 diff，可见三级标题开始的内容被删除，项目用途句出现重复标点。

## Evidence
- merge_existing_file 使用换行后双井号作为前瞻，但未限制后续字符，因此会在三级标题处提前结束匹配。

## Environment Notes
- Skill source path: None
- Skill source repo: huangwb8/bensz-skills
- Device type: desktop
- OS: Darwin / 25.6.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex CLI
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v22.11.0
  - npm: 10.9.0
  - python3: Python 3.9.6
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
保存合并前版本，运行生成器后用精确补丁恢复被截断的自定义内容、修复重复标点，再校验必需章节。

## Additional Notes
仅本地记录，未公开上传。
