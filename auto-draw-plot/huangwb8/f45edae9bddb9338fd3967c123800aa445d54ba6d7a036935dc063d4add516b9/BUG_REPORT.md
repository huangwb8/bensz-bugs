# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: f45edae9bddb9338fd3967c123800aa445d54ba6d7a036935dc063d4add516b9
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-14T15:02:05Z
- Last seen at: 2026-07-14T15:02:05Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
gpt-image-2 async edits endpoint rejects skill multipart request as malformed JSON

## Expected Behavior
When a reference PNG is supplied for round-two image-to-image refinement, the skill should submit a valid edit job and return an edited PNG.

## Actual Behavior
The configured async edits endpoint returns HTTP 400 invalid_request_error with message Malformed JSON request body before creating a job.

## Reproduction Steps
- Generate a successful first-round PNG with gpt-image-2.
- Call generate_image.py with --reference-image, --provider gpt-image-2, and --require-reference-images.

## Evidence
- HTTP 400 Bad Request; code=invalid_request_error; Malformed JSON request body.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
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
Preserve the successful first-round PNG and add exact labels deterministically with a local raster overlay.

## Additional Notes
None
