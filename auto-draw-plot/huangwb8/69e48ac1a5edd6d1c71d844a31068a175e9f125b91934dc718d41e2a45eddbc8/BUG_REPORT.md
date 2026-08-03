# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 69e48ac1a5edd6d1c71d844a31068a175e9f125b91934dc718d41e2a45eddbc8
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-01T03:05:58Z
- Last seen at: 2026-08-01T03:05:58Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Async image job can leave the draw script with exit code zero but no output image

## Expected Behavior
If an accepted async image job is still running, the workflow should continue polling according to its configured wait policy or exit nonzero with a safe resumable failure record.

## Actual Behavior
The workflow submitted one gpt-image-2 job and recorded running polls, then exited successfully without output.jpg, result metadata, or the requested public JPEG.

## Reproduction Steps
- Run auto-draw-plot with the default async gpt-image-2 job endpoint and a valid general-mode request.
- Observe a job that remains running past the script polling window.
- Confirm the process exits zero while the requested output file is absent.

## Evidence
- The run manifest records a queued async job and the poll log ends with status running; no generated image or final result metadata exists.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.6.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
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
Do not resubmit. Poll the existing job read-only until terminal, then download its result through the provider client or retry only after the job is terminal.

## Additional Notes
None
