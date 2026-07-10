# Bug Report

## Metadata
- Skill: validate-md-ref
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 9ab025b0a7c7a4d2d89603a0d0825681077e5f10919ad4d83ad639bbb1729c94
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-10T14:39:01Z
- Last seen at: 2026-07-10T14:39:01Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
HEAD-only URL validation misclassifies GET-accessible links as invalid

## Expected Behavior
Treat URLs as valid when a normal GET request succeeds, including sites that reject HEAD with 403 or 405.

## Actual Behavior
The validator uses curl -I only and marks Hacker News URLs returning HEAD 405 plus anti-bot-protected official pages returning HEAD 403 as invalid even though GET retrieval succeeds.

## Reproduction Steps
- Run validate_links.py against a Markdown file containing a Hacker News item URL.
- Observe HTTP 405 invalid, then fetch the same URL with GET and receive readable content.

## Evidence
- Summary reported 53 invalid of 125; most were HEAD 405 for Hacker News or HEAD 403 for accessible anti-bot pages.

## Environment Notes
- Skill source path: None
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
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Recheck HEAD failures with GET and distinguish access-control responses from true 404 or DNS failures.

## Additional Notes
None
