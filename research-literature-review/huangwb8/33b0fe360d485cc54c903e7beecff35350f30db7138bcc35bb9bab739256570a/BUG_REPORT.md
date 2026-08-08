# Bug Report

## Metadata
- Skill: research-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 33b0fe360d485cc54c903e7beecff35350f30db7138bcc35bb9bab739256570a
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-07T12:37:19Z
- Last seen at: 2026-08-07T12:37:19Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
pipeline_runner passes relative config path to child running under work_dir causing duplicated path

## Expected Behavior
A config path accepted by pipeline_runner should remain valid in plan_word_budget and later child stages.

## Actual Behavior
A relative config path is re-resolved under the work directory and becomes work_dir/work_dir/output/config, causing FileNotFoundError.

## Reproduction Steps
- Start pipeline_runner from the project root with --work-dir TASK and --config TASK/output/config.yaml.
- Reach stage 4.5 where plan_word_budget is invoked with cwd set to TASK.

## Evidence
- The child attempted TASK/TASK/output/config.yaml although TASK/output/config.yaml exists.

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
Pass an absolute config path to pipeline_runner.

## Additional Notes
None
