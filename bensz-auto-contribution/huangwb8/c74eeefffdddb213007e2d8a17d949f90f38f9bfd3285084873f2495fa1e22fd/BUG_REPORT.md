# Bug Report

## Metadata
- Skill: bensz-auto-contribution
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: c74eeefffdddb213007e2d8a17d949f90f38f9bfd3285084873f2495fa1e22fd
- Severity: important
- Occurrence count: 1
- First seen at: 2026-10-04T00:30:56Z
- Last seen at: 2026-10-04T00:30:56Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Git remote 配置变化导致 BAC 项目指纹漂移，record 成功后账本反而校验失败

## Expected Behavior
同一目录在 Git 初始化及配置远程后仍能继续记账；拒绝写入会破坏账本不变量的事件

## Actual Behavior
root_hash 同时包含 root_path 和 git_remote；原始 genesis 没有远程，新事件有远程，record 未阻止写入，verify 失败并阻断后续追加

## Reproduction Steps
- 在尚无 Git remote 的工作区创建 BAC genesis
- 在同一目录初始化 Git 或添加 remote
- record 一条事件成功后运行 verify

## Evidence
- project.root_hash changed within ledger；源码 collect_project_context 使用 root_path 与 git_remote 计算指纹

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex CLI
- Key software versions:
  - bensz-auto-contribution: 1.3.2
  - claude: unavailable
  - codex: codex-cli 0.159.2
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.2.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
保留原始账本，不重写历史或手工伪造哈希；本轮待补记摘要暂存本地任务记录

## Additional Notes
None
