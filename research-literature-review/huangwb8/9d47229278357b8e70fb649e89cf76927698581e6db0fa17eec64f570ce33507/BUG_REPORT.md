# Bug Report

## Metadata
- Skill: research-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 9d47229278357b8e70fb649e89cf76927698581e6db0fa17eec64f570ce33507
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-02T08:38:06Z
- Last seen at: 2026-08-02T08:38:06Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
pipeline_runner 字数预算阶段把安装目录配置传给仅允许工作目录路径的子脚本

## Expected Behavior
使用 --work-dir 启动的 Premium 流水线应能在阶段 4.5 读取配置并生成字数预算。

## Actual Behavior
pipeline_runner 将 skill 安装目录中的 config.yaml 传入 plan_word_budget.py，后者的 path_scope 拒绝工作目录外路径，阶段 4.5 必然失败。

## Reproduction Steps
- 以显式 --work-dir 启动 pipeline_runner 并完成评分与选文。
- 从阶段 3 或阶段 4 恢复，进入 4.5_word_budget。

## Evidence
- ValueError: config.yaml 路径不在工作目录内；工作目录隔离检查终止 plan_word_budget.py。

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
把 config.yaml 复制到当前工作目录 input 子目录，并用 --config 指向该副本后恢复流水线。

## Additional Notes
None
