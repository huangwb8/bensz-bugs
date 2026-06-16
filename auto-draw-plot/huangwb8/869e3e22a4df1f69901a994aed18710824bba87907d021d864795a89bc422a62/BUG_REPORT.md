# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 869e3e22a4df1f69901a994aed18710824bba87907d021d864795a89bc422a62
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-06-06T13:39:25Z
- Last seen at: 2026-06-06T13:39:25Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
roadmap/schematic gpt-image-2 bridge 502/504 causes long retry loop before provider fallback

## Expected Behavior
When gpt-image-2 via BenszAPI returns repeated upstream 502/504 for diagram-style requests, auto-draw-plot should classify the failure quickly and fall back to Nano Banana/Gemini, or expose a concise actionable error without waiting through long retry-after delays.

## Actual Behavior
In roadmap mode, a valid gpt-image-2 Images request with size 1024x1024 received HTTP 504 after the upstream bridge recorded provider 502 around 90 seconds; the script treated it as temporarily unavailable and planned another retry after 120 seconds, delaying fallback.

## Reproduction Steps
- Run auto-draw-plot in roadmap mode with a simple Chinese labelled cat roadmap request and max_rounds=1 using a BenszAPI gpt-image-2 provider backed by OAuth Images bridge.
- Observe gpt-image-2 HTTP 504 and the warning that it will retry after 120 seconds instead of quickly falling back to Nano Banana/Gemini.

## Evidence
- Local debug request used model gpt-image-2, size 1024x1024, n=1; remote ops recorded upstream/provider HTTP 502 on /v1/responses after about 90 seconds. Size was valid, so this was not an invalid-size error.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
- Key software versions:
  - claude: 2.1.167 (Claude Code)
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
Use a dedicated image group/provider with stable API-key image upstream, or make auto-draw-plot prefer Nano Banana/Gemini for roadmap/schematic until gpt-image-2 bridge stability improves.

## Additional Notes
None
