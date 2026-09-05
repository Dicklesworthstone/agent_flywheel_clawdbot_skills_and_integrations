---
name: ru
description: "Inspect or synchronize repositories with RU, or run a requested multi-repository review."
---

# Repo Updater

Resolve the repository set and inspect status first. Use dry-run or plan mode before a requested batch mutation. Apply, commit, push, release, and prune only within the task's authority; preserve unrelated work. Finish when results for every targeted repository are accounted for, with failures and skipped work reported.

## Start

Resolve the target and read the matching reference section below. Check the
installed command's help when a flag or version differs from the examples.
Paths in examples are relative to this skill directory unless stated otherwise.

```bash
ru status --json
```

## Task reference

Read the section matching the task; the full command manual is retained for
lookup rather than loaded for every invocation.

| Task | Reference |
|------|-----------|
| Inspect or sync repositories | [Manual](references/MANUAL.md#essential-commands) |
| Plan and apply reviews | [Manual](references/MANUAL.md#ai-assisted-review-system) |
| Process owned dirty work | [Manual](references/MANUAL.md#agent-sweep-automated-dirty-repo-processing) |
| Configuration | [Manual](references/MANUAL.md#configuration) |
| Failures and exit codes | [Manual](references/MANUAL.md#exit-codes-sync) |
| Installation | [Manual](references/MANUAL.md#installation) |

## Verification

Verify the requested result using the relevant read surface. Report errors,
partial results, and remaining uncertainty. Repeat checks only after a change
or new evidence requires it.
