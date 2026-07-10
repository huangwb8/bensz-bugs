# Bug Report

## Metadata
- Skill: install-bensz-skills
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: f6ad8eaf837b6fa458897e080cf3073219dbb6e93931c7af5899d43630158f09
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-04T06:29:16Z
- Last seen at: 2026-07-04T06:29:16Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Remote install cloned entire large repository even when skills_path targeted a subdirectory

## Expected Behavior
When a remote source sets skills_path to a subdirectory such as skills, the installer should download only that target skill subtree when possible.

## Actual Behavior
The remote download path always ran a shallow clone of the whole repository first, then resolved skills_path locally, so a large repository such as ChineseResearchLaTeX downloaded unrelated non-skill content.

## Reproduction Steps
- Configure a remote source with url https://github.com/huangwb8/ChineseResearchLaTeX and skills_path skills.
- Run install-bensz-skills in remote check or auto mode for the research source.

## Evidence
- _download_remote_source used git clone --depth 1 for the full repository before calling _resolve_remote_skills_root(repo_root, skills_path).

## Environment Notes
- Skill source path: None
- Skill source repo: huangwb8/skills
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex CLI
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
Patch the project source so non-root skills_path uses git clone --filter=blob:none --sparse followed by git sparse-checkout set <skills_path>, with full shallow clone fallback.

## Additional Notes
Fixed in project source version 0.5.6; no installed system-level skill source was edited.
