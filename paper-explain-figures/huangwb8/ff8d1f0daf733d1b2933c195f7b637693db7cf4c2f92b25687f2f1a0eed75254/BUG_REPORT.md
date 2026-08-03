# Bug Report

## Metadata
- Skill: paper-explain-figures
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: ff8d1f0daf733d1b2933c195f7b637693db7cf4c2f92b25687f2f1a0eed75254
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-26T00:22:33Z
- Last seen at: 2026-07-26T00:22:33Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
macOS .DS_Store causes workspace-leak audit failure despite no user-file mutation

## Expected Behavior
A figure explanation run should complete when only OS-generated .DS_Store appears outside the designated intermediate directory.

## Actual Behavior
The runner terminated with an unauthorized-path error for .DS_Store and did not write the figure report.

## Reproduction Steps
- Run paper_explain_figures.py on a PNG figure from a macOS workspace.
- Allow the runner to perform its normal workspace audit after job completion.

## Evidence
- Error: [ERROR] 检测到工作目录中存在被修改的非授权路径：.DS_Store

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex CLI
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
Use the source figure and caption directly; consider ignoring or redirecting .DS_Store in the audit.

## Additional Notes
None
