# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: c57644ef2b9969d71665988e90ffc88cbeec51ca2efa1ffdff446fca146a4aa8
- Severity: minor
- Occurrence count: 1
- First seen at: 2026-07-21T12:36:10Z
- Last seen at: 2026-07-21T12:36:10Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Pandoc 自动引导失败后未提供可用渲染路径

## Expected Behavior
当系统 Pandoc 缺失时，技能应安装并使用可用 Pandoc 完成 Rmd 渲染。

## Actual Behavior
执行渲染脚本后以“pandoc binary not found after installation”退出。

## Reproduction Steps
- 确保 Rscript 可用且 Pandoc 不在 PATH。
- 执行 knit_rmd_html.py 对一个 Rmd 进行渲染。

## Evidence
- 脚本以 exit code 1 退出，输出 pandoc binary not found after installation。

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
使用本机 R 的 rmarkdown::render() 并显式设置 knit_root_dir；在运行前提供可用 Pandoc 路径。

## Additional Notes
None
