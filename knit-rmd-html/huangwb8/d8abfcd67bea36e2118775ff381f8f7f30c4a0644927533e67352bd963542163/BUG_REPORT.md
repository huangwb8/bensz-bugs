# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: d8abfcd67bea36e2118775ff381f8f7f30c4a0644927533e67352bd963542163
- Severity: high
- Occurrence count: 1
- First seen at: 2026-08-09T06:09:10Z
- Last seen at: 2026-08-09T06:09:10Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc ZIP 布局与自动安装脚本预期不一致

## Expected Behavior
Windows Pandoc ZIP 解压后应定位实际 pandoc.exe，并在自动安装完成后继续渲染。

## Actual Behavior
脚本固定查找版本目录下的 bin/pandoc，但当前官方 Windows ZIP 将 pandoc.exe 放在版本目录根部，因而错误报告二进制不存在。

## Reproduction Steps
- 在 PATH 不含 Pandoc 的 Windows 环境运行 knit_rmd_html.py。
- 允许脚本下载并解压官方 Windows Pandoc ZIP。

## Evidence
- 解压目录存在可运行的 pandoc.exe，但脚本报告 pandoc binary not found after installation。

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
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
把已有 pandoc.exe 所在目录和 R_HOME/bin 临时加入渲染子进程 PATH，并使用 --no-install。

## Additional Notes
None
