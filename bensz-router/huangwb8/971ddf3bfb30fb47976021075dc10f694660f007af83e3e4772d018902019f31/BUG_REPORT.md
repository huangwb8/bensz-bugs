# Bug Report

## Metadata
- Skill: bensz-router
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 971ddf3bfb30fb47976021075dc10f694660f007af83e3e4772d018902019f31
- Severity: important
- Occurrence count: 1
- First seen at: 2026-10-07T10:14:43Z
- Last seen at: 2026-10-07T10:14:43Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows MCP uses the locale encoding instead of UTF-8 and doctor can falsely report success

## Expected Behavior
MCP stdio must emit valid UTF-8 JSON, and diagnostic checks must verify that wire encoding.

## Actual Behavior
Version 1.1.4 emits non-UTF-8 tool descriptions under the default Windows locale, while hooks doctor reports process_verified and tools_verified true.

## Reproduction Steps
- On Windows with the default Python locale encoding, initialize the MCP server and request tools/list, capturing stdout as bytes.
- Decode the captured response strictly as UTF-8 and compare the result after setting PYTHONUTF8=1.

## Evidence
- Minimal wire check: default environment exit_code=0 and mcp_wire_valid_utf8_json=false; PYTHONUTF8=1 exit_code=0 and mcp_wire_valid_utf8_json=true. mcp.py uses sys.stdout and ensure_ascii=False; mcp_setup.py probes using locale text decoding.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: workstation
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - bensz-router: 1.1.4
  - claude: unavailable
  - codex: codex-cli 0.162.0-alpha.2
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.2.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Set user-level PYTHONUTF8=1 and restart the host so MCP, hooks and diagnostics inherit UTF-8 mode. Independent strict UTF-8 wire verification and doctor then pass.

## Additional Notes
None
