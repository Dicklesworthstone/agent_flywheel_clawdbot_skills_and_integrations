---
name: github
description: "Use GitHub CLI to inspect repositories, pull requests, issues, Actions, or perform requested GitHub changes."
---

# GitHub CLI

Inspect the target repository and current state before changing GitHub resources. Reading a workflow example does not authorize posting messages, publishing, merging, deleting, or changing access. Follow existing task authority and repository policy. Finish when an authoritative read confirms the requested change or the requested evidence is reported.

## Start

Resolve the target and read the matching reference section below. Check the
installed command's help when a flag or version differs from the examples.
Paths in examples are relative to this skill directory unless stated otherwise.

```bash
gh auth status
```

## Task reference

Read the section matching the task; the full command manual is retained for
lookup rather than loaded for every invocation.

| Task | Reference |
|------|-----------|
| Repositories | [Manual](references/MANUAL.md#repositories) |
| Issues | [Manual](references/MANUAL.md#issues) |
| Pull requests | [Manual](references/MANUAL.md#pull-requests) |
| CI and Actions | [Manual](references/MANUAL.md#actions-cicd) |
| Releases | [Manual](references/MANUAL.md#releases) |
| API calls | [Manual](references/MANUAL.md#api) |
| Workflow examples | [Manual](references/MANUAL.md#common-workflows) |

## Verification

Verify the requested result using the relevant read surface. Report errors,
partial results, and remaining uncertainty. Repeat checks only after a change
or new evidence requires it.
