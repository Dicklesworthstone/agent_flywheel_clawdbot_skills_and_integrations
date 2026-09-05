---
name: cass
description: "Search prior agent sessions, recover a session, or diagnose the CASS history index."
dependencies:
  - "cass binary (>=0.3.6 recommended; some commands require HEAD — see Version Pinning)"
  - "jq (required for parsing --json output)"
  - "GNU coreutils 'timeout' (recommended; cass index can hang under contention)"
  - "ssh + rsync (optional; only for cross-machine `cass sources` workflows)"
  - "fastembed model bundle ~90MB (optional; only for --mode semantic / hybrid; install via `cass models install`)"
harmonized_against:
  tool_version: 0.6.26
  verified: installed-binary probe (cass --version)
  date: 2026-08-25
---

# CASS Session Search

Search a usable index immediately. If recovery is needed and authorized, use scripts/recover.sh from this skill directory; its index operations are time-bounded. If recovery fails, report the limitation and use scoped source-session search when useful. Source deletion, configuration changes, remote sync, and session resumption require task authority. Finish with relevant evidence and coverage limits, rather than repeated repair attempts.

## Start

Resolve the target and read the matching reference section below. Check the
installed command's help when a flag or version differs from the examples.
Paths in examples are relative to this skill directory unless stated otherwise.

```bash
timeout 15 cass status --json
cass search "KEYWORD" --workspace /path --json --fields minimal --limit 10
```

## Task reference

Read the section matching the task; the full command manual is retained for
lookup rather than loaded for every invocation.

| Task | Reference |
|------|-----------|
| Search workflow | [Manual](references/MANUAL.md#the-exact-prompt--discovery-workflow) |
| Index health and bounded recovery | [Manual](references/MANUAL.md#two-step-bootstrap-replaces-always-first) |
| Search modes and flags | [Manual](references/MANUAL.md#quick-reference) |
| Cross-machine history | [Manual](references/MANUAL.md#cross-machine-search-multi-workstation-corpus) |
| Resume a past session | [Manual](references/MANUAL.md#resume-a-past-session-in-its-native-harness) |
| Recovery authority | [Manual](references/MANUAL.md#recovery-cheat-sheet-no-permission-moves) |
| Detailed task references | [Manual](references/MANUAL.md#reference-index) |

## Verification

Verify the requested result using the relevant read surface. Report errors,
partial results, and remaining uncertainty. Repeat checks only after a change
or new evidence requires it.
