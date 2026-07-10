# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: c1ee56d383158e3b317f6c48dcc0b95766918e47609906ae831afaf2e5cdfd56
- Severity: important
- Occurrence count: 1
- First seen at: 2026-06-29T08:52:37Z
- Last seen at: 2026-06-29T08:52:37Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
gpt-image-2 image-to-image edit request returns malformed JSON in auto-draw-plot

## Expected Behavior
When a reference image is supplied for round two, auto-draw-plot should submit a valid image edit request or fail with a clear provider contract error before sending the request.

## Actual Behavior
With provider gpt-image-2 and a reference PNG, run_draw_plot.py submitted the edit request and failed with HTTP 400 Bad Request: Malformed JSON request body, stopping multi-round optimization.

## Reproduction Steps
- Generate a first-round PNG with run_draw_plot.py using provider gpt-image-2.
- Run run_draw_plot.py again with --reference-image pointing to the previous PNG and provider gpt-image-2.

## Evidence
- ProviderHTTPError: HTTP 400 Bad Request: {"error":{"code":"invalid_request_error","message":"Malformed JSON request body","type":"invalid_request_error"}}

## Environment Notes
- Skill source path: None
- Skill source repo: local codex skill auto-draw-plot
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
- Key software versions:
  - claude: 2.1.181 (Claude Code)
  - codex: codex-cli 0.137.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Run a fresh text-to-image generation with the same provider, then use local deterministic post-processing for exact Chinese labels when necessary.

## Additional Notes
None
