# Bug Report

## Metadata
- Skill: research-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: bafc6ca201f9de9cb7559f46df40e6675584eaddf5efc8a156c6423fafba8e3a
- Severity: critical
- Occurrence count: 1
- First seen at: 2026-08-02T08:39:11Z
- Last seen at: 2026-08-02T08:39:11Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
pipeline_runner 使用 --resume-from 时跳过加载已有状态并覆盖 pipeline_state

## Expected Behavior
同时提供 --resume 与 --resume-from 时应先加载已有 pipeline_state，再从指定阶段继续。

## Actual Behavior
run() 仅在 resume_from 为空时加载状态；指定 resume_from 后使用全新空状态，导致 selected_papers 等输入路径丢失，并在失败时覆盖原状态。

## Reproduction Steps
- 完成检索、评分和选文并保存 pipeline_state。
- 执行 pipeline_runner --resume WORK_DIR --resume-from 5。

## Evidence
- 阶段 4.5 收到 --selected .；新 pipeline_state 的 completed_stages、input_files 与 output_files 均为空。

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.6.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
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
不依赖 --resume-from 恢复；改为直接调用阶段脚本并使用工作目录内绝对路径，或先修复/重建状态。

## Additional Notes
None
