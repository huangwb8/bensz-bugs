# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 46ad4166493750971415ad9347d89a50a14a29f4bc1bd178563e6ad3b16fec58
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-18T10:27:16Z
- Last seen at: 2026-07-18T10:27:16Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Non-idempotent image submit retries treat static pricing failures as transient HTTP 503

## Expected Behavior
Static billing or pricing configuration failures should stop immediately using a stable structured error code; uncertain submit retries should reuse an idempotency key.

## Actual Behavior
A generic HTTP 503 with a balance reservation pricing message is classified as transient and retried up to five times without an idempotency key.

## Reproduction Steps
- Submit a gpt-image-2 job while the backend cannot resolve reservation pricing.
- Observe the transient classification and repeated POST policy.

## Evidence
- The final sanitized error is HTTP 503 api_error with a pricing unavailable message; retry policy classifies 503 as transient.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
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
Return a stable billing pricing code from the backend, stop non-retryable pricing failures, and add a stable idempotency key for retryable submits.

## Additional Notes
None
