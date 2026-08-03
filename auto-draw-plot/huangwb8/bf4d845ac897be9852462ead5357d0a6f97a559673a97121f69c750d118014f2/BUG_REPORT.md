# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: bf4d845ac897be9852462ead5357d0a6f97a559673a97121f69c750d118014f2
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-14T14:23:30Z
- Last seen at: 2026-07-14T14:23:30Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
provider health check overstates image generation eligibility and structured billing errors lack stable classification

## Expected Behavior
The models probe should report only connectivity and authentication; the real image submit response should be the eligibility decision, preserving safe type, code, and message fields, and policy errors should stop without provider fallback.

## Actual Behavior
A successful models probe can be interpreted as image-generation availability, while immediate async-submit billing failures and terminal job errors are not consistently exposed as stable structured client-policy errors; provider fallback can therefore obscure the real rejection.

## Reproduction Steps
- Return HTTP 200 from the models endpoint for a valid API key.
- Return a structured HTTP 403 SUBSCRIPTION_REQUIRED response from the async image submit endpoint.
- Observe that preflight wording and error/fallback behavior do not clearly preserve the final admission decision.

## Evidence
- The source health check probes models before submission; ProviderHTTPError stores only status, reason, and raw detail; generation fallback catches a broad exception.

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
Treat the real image submit as authoritative, inspect the structured OpenAI error payload, and do not switch providers for billing or permission rejections.

## Additional Notes
None
