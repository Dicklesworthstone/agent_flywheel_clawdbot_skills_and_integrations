---
name: cm
description: "Retrieve prior decisions with CASS Memory, record feedback, or maintain its playbook."
---

# CASS Memory

Read-only retrieval is appropriate when prior decisions matter. Memory writes, reflection, privacy changes, and installations need task authority. Treat retrieved rules as evidence subject to current instructions. Finish when the requested context or verified memory change is delivered.

## Start

Resolve the target and read the matching reference section below. Check the
installed command's help when a flag or version differs from the examples.
Paths in examples are relative to this skill directory unless stated otherwise.

```bash
cm context "<task>" --json
```

## Task reference

Read the section matching the task; the full command manual is retained for
lookup rather than loaded for every invocation.

| Task | Reference |
|------|-----------|
| Retrieve task context | [Manual](references/MANUAL.md#the-one-command-you-need) |
| Commands and feedback | [Manual](references/MANUAL.md#commands-reference) |
| Memory workflow | [Manual](references/MANUAL.md#agent-protocol) |
| Configuration and budgets | [Manual](references/MANUAL.md#configuration) |
| Privacy and cross-agent consent | [Manual](references/MANUAL.md#privacy--security) |
| Installation or repair | [Manual](references/MANUAL.md#troubleshooting) |

## Verification

Verify the requested result using the relevant read surface. Report errors,
partial results, and remaining uncertainty. Repeat checks only after a change
or new evidence requires it.
