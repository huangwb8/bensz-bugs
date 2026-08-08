# Bug Report

## Metadata
- Skill: research-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 397bd118b6ea8f03a638f022e977bd5056498001c50c55cfb0fc6ca0970ba1d9
- Severity: critical
- Occurrence count: 1
- First seen at: 2026-08-07T12:37:20Z
- Last seen at: 2026-08-07T12:37:20Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
combining --resume and --resume-from skips loading pipeline state and can overwrite checkpoints

## Expected Behavior
Explicit resume-from should load the saved state and then restart at the requested stage.

## Actual Behavior
PipelineRunner.run only loads state when resume_from is None; with both flags the in-memory empty state is used and saved over the prior checkpoint.

## Reproduction Steps
- Complete search and save pipeline state.
- Invoke pipeline_runner with --resume TASK --resume-from 2.

## Evidence
- Stage 2 received input path dot and pipeline_state.json was overwritten with an empty completed_stages list.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: desktop
- OS: Darwin / 25.6.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v22.11.0
  - npm: 10.9.0
  - python3: 3.9.6
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Use --resume without --resume-from so the runner loads state and advances from the last completed stage.

## Additional Notes
None
