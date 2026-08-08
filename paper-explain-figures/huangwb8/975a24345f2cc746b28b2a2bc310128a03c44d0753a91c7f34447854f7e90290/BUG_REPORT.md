# Bug Report

## Metadata
- Skill: paper-explain-figures
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 975a24345f2cc746b28b2a2bc310128a03c44d0753a91c7f34447854f7e90290
- Severity: minor
- Occurrence count: 1
- First seen at: 2026-07-20T01:36:24Z
- Last seen at: 2026-07-20T01:36:24Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
运行产物未落入调用方指定的任务目录

## Expected Behavior
脚本应将中间产物写入当前任务的 paper-explain-figures 子目录。

## Actual Behavior
脚本输出到 .bensz-api/skills/paper-explain-figures/ 下的独立目录，未使用当前任务目录。

## Reproduction Steps
- 在一个含 .bensz-api/task-YYYYMMDD-HHMM-描述/ 的工作区执行 paper_explain_figures.py。
- 传入一个本地图片并使用 local runner。

## Evidence
- 命令成功后输出的中间路径为 .bensz-api/skills/paper-explain-figures/YYYY-MM-DD-HH-MM。

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: codex
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
保留该路径作为本次工具运行证据，并在主任务目录记录引用；不要将用户项目文件写入该处。

## Additional Notes
None
