# Bug Report

## Metadata
- Skill: init-project
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: f7e39ef31040425ec373cea217573892e4464cdfdaa9de3208083396b3883ec3
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-23T11:13:47Z
- Last seen at: 2026-07-23T11:13:47Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows 中文代码页下默认 BAC 初始化的 emoji 输出触发 UnicodeEncodeError

## Expected Behavior
自动初始化应检查或安装 BAC 依赖并继续生成项目文件。

## Actual Behavior
在缺少 BAC 包的 Windows 中文代码页环境中，脚本打印 emoji 时因 GBK 无法编码而中止。

## Reproduction Steps
- 在 Windows 中文代码页环境确认未安装 bac 包。
- 运行 generate.py --auto 指向当前项目目录。

## Evidence
- ensure_bac_dependency 打印 U+1F4E6 时抛出 UnicodeEncodeError: gbk codec can't encode character，退出码为 1。

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: desktop
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
  - python: 3
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
运行前设置 PYTHONIOENCODING=utf-8，并显式设置 PowerShell 控制台输出编码为 UTF-8。

## Additional Notes
None
