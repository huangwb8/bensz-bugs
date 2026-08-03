# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 1c60e14c8421c21be3ac32003ec2274b69f371af71aa434105a83e4951ac190a
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-18T10:27:15Z
- Last seen at: 2026-07-18T10:27:15Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
gpt-image-2 provider controls and JPEG delivery are not represented by the skill contract

## Expected Behavior
When the user requests lowest quality, smallest native size, and JPEG output, the skill should send explicit provider parameters and deliver bytes whose MIME and extension match JPEG.

## Actual Behavior
The skill sends model, prompt, size, and n only; quality is merely prompt text, and the workflow is PNG-only.

## Reproduction Steps
- Run a gpt-image-2 generation requesting low quality and JPEG.
- Inspect the sanitized request metadata and final output contract.

## Evidence
- Request metadata contains no quality or output_format; the CLI and workflow expose only output_png.

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
Keep PNG as a canonical intermediate, add explicit validated provider controls, then export JPEG with matching MIME, extension, and metadata.

## Additional Notes
None
