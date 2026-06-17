# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 8c767314d8e7f4e9b9ecfd4c8c42d0ee259a6ec355da7f8b67eed391c21cbc4a
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-06-17T13:03:46Z
- Last seen at: 2026-06-17T13:03:46Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
gpt-image-2 image-to-image round fails with malformed JSON request body

## Expected Behavior
When round 1 does not pass heuristic evaluation, auto-draw-plot should use the previous PNG as a reference and complete the next gpt-image-2 image edit round or report a provider-specific unsupported edit mode cleanly.

## Actual Behavior
Round 1 generated a valid PNG, but round 2 image-to-image edit failed at the gpt-image-2 edits job endpoint with HTTP 400 Malformed JSON request body, aborting the run before final result metadata was written.

## Reproduction Steps
- Run auto-draw-plot in schematic mode with gpt-image-2 and max_rounds greater than 1.
- Allow round 1 to complete and trigger round 2 image-to-image editing using the previous output PNG as reference.

## Evidence
- HTTP 400 Bad Request: Malformed JSON request body from gpt-image-2 edits endpoint during round 2.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
- Key software versions:
  - claude: 2.1.50 (Claude Code)
  - codex: codex-cli 0.124.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v24.11.1
  - npm: 11.6.2
  - python3: Python 3.13.11
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Use the valid round-01 output as final when acceptable, or rerun with max_rounds=1 to avoid the edit endpoint.

## Additional Notes
None
