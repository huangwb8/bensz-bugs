# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 0b3829790f3825eebabd23ca5867a72399487ccc640e3d7845a869611f47da25
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-06T07:34:28Z
- Last seen at: 2026-08-06T07:34:28Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc ZIP 安装后无法定位可执行文件

## Expected Behavior
自动安装 Windows Pandoc 后应发现可执行文件并继续渲染 R Markdown。

## Actual Behavior
Pandoc ZIP 已下载并解压，但脚本按固定子目录和无扩展名文件定位，最终报告 pandoc binary not found after installation。

## Reproduction Steps
- 在 Windows 且 PATH 中无 pandoc 时调用 knit_rmd_html.py 渲染任意 Rmd。
- 允许脚本自动下载并解压默认 Pandoc ZIP。

## Evidence
- 错误信息：[pandoc] pandoc binary not found after installation.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: desktop
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: codex
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
使用本机 RStudio 内置 Pandoc，设置 RSTUDIO_PANDOC 后直接调用 rmarkdown::render。

## Additional Notes
None
