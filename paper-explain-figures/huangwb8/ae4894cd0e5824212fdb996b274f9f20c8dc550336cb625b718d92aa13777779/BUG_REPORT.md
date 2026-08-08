# Bug Report

## Metadata
- Skill: paper-explain-figures
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: ae4894cd0e5824212fdb996b274f9f20c8dc550336cb625b718d92aa13777779
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-22T17:09:08Z
- Last seen at: 2026-07-22T17:09:08Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
运行脚本仍使用旧版隐藏工作目录，与当前任务级目录契约不一致

## Expected Behavior
脚本应将中间产物写入当前任务根目录下的 paper-explain-figures 边界

## Actual Behavior
脚本常量仍指向 .bensz-api/skills/paper-explain-figures，可能绕过统一任务归档

## Reproduction Steps
- 读取当前 SKILL.md 的任务工作区约定
- 检查 scripts/paper_explain_figures.py 中 WORK_DIR_REL 常量

## Evidence
- 文档要求 task 级目录，脚本使用 skills 级旧路径

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.144.0-alpha.4
  - gh: unavailable
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
从本轮任务根目录内运行脚本，使旧路径仍被包在单一任务目录中，并记录目录映射

## Additional Notes
None
