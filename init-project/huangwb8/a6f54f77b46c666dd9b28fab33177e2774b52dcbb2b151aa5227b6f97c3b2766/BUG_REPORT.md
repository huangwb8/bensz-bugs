# Bug Report

## Metadata
- Skill: init-project
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: a6f54f77b46c666dd9b28fab33177e2774b52dcbb2b151aa5227b6f97c3b2766
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-01T14:00:28Z
- Last seen at: 2026-08-01T14:00:28Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows GBK 控制台输出 Unicode 状态图标导致初始化中止

## Expected Behavior
生成器应在 Windows 默认控制台编码下完成 BAC 检查与项目初始化

## Actual Behavior
检测到 bac 包后输出 Unicode 对勾字符并触发 UnicodeEncodeError，流程在写入项目文档前中止

## Reproduction Steps
- 在 Windows PowerShell 中以默认 Python 输出编码运行 generate.py --auto
- 进入 ensure_bac_dependency 并输出已检测到 bac 包的状态信息

## Evidence
- UnicodeEncodeError: gbk codec cannot encode check-mark character in ensure_bac_dependency

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
运行前设置 PYTHONUTF8=1，使 Python 标准输出使用 UTF-8

## Additional Notes
None
