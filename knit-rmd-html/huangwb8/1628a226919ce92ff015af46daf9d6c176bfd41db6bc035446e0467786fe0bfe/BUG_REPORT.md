# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 1628a226919ce92ff015af46daf9d6c176bfd41db6bc035446e0467786fe0bfe
- Severity: minor
- Occurrence count: 1
- First seen at: 2026-07-21T12:37:59Z
- Last seen at: 2026-07-21T12:37:59Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows 下包装器以 GBK 解码 R 的 UTF-8 输出导致渲染崩溃

## Expected Behavior
渲染包装器应能解码 R 的 UTF-8 输出并返回渲染结果。

## Actual Behavior
R 子进程启动后，Python subprocess 读取输出时抛出 UnicodeDecodeError gbk codec cannot decode byte。

## Reproduction Steps
- 在 Windows 上设置可用 Rscript 与 pandoc.exe。
- 执行 knit_rmd_html.py 渲染包含 UTF-8 输出的 Rmd。

## Evidence
- Traceback 指向 subprocess.py stdout.read()，错误为 UnicodeDecodeError gbk codec cannot decode byte 0x80。

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
跳过 Python 包装器，直接以 Rscript 调用 rmarkdown::render()，并在 PATH 中提供 Pandoc。

## Additional Notes
None
