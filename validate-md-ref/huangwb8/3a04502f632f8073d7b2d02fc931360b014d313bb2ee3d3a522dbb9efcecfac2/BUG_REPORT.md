# Bug Report

## Metadata
- Skill: validate-md-ref
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 3a04502f632f8073d7b2d02fc931360b014d313bb2ee3d3a522dbb9efcecfac2
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-12T11:24:51Z
- Last seen at: 2026-07-12T11:24:51Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
站内锚点被当作非法外部 URL 并计入无效链接

## Expected Behavior
仅对 http/https 外部链接执行网络检查，并单独校验 #refN 站内锚点是否存在

## Actual Behavior
脚本把合法的 #refN 链接标记为 URL 格式非法，并计入 invalid，导致有效率严重失真

## Reproduction Steps
- 在 Markdown 中加入正文引用 [1](#ref1) 和对应的 HTML 锚点
- 运行 scripts/validate_links.py 检查该文档

## Evidence
- 24 个合法 #refN 站内锚点均被报告为 URL 格式非法

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
忽略脚本对 # 开头链接的网络校验结果，另用文本匹配核对引用和锚点集合

## Additional Notes
None
