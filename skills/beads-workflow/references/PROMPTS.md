# Complete Beads Prompt Reference

## Table of Contents
- [Plan to Beads Conversion](#plan-to-beads-conversion)
- [Polishing Prompts](#polishing-prompts)
- [Fresh Session Prompts](#fresh-session-prompts)
- [Test Coverage](#test-coverage)

---

## Plan to Beads Conversion

### Example Prompt — Full Version

```
Convert the accepted plan into bounded tasks with acceptance criteria, dependencies, ownership, and the rationale needed for implementation. Preserve the agreed scope. Use the repository's supported issue tool and safe-write protocol only when issue creation is authorized.
```

**Replace** `[YOUR_PLAN_FILE].md` with your actual plan filename.

### Example Prompt — Short Version

```
Convert the accepted plan into scoped tasks with acceptance criteria and dependencies using the repository's authorized issue workflow.
```

**Use when:** Plan is already in context from earlier conversation.

---

## Polishing Prompts

### Example Prompt — Polish (Standard)

```
Review the assigned plan and its task graph against the requested scope, dependencies, and acceptance criteria. Report concrete omissions or conflicts. Revise records only when edits are authorized; keep additional ideas separate.

DO NOT OVERSIMPLIFY THINGS! DO NOT LOSE ANY FEATURES OR FUNCTIONALITY!

Include verification appropriate to the planned behavior and material regression risks. Preserve the plan's required outcomes without adding unrelated test work.
```

### Example Prompt — Polish (Full with Plan Reference)

```
Review the assigned plan and its task graph against the requested scope, dependencies, and acceptance criteria. Report concrete omissions or conflicts. Revise records only when edits are authorized; keep additional ideas separate.
```

**Use when:** You want to ensure nothing from the original plan was lost.

### Polishing Protocol

```
Review → Check scope, acceptance criteria, and dependency correctness
Revise → Resolve material findings
Verify → Check changed tasks and their dependencies
Finish → All requested tasks are implementable and findings resolved

Another reviewer → Use when uncertainty or risk warrants an independent check
```

---

## Fresh Session Prompts

When a specific unresolved finding needs fresh context or expertise, transfer
its evidence and scope to a capable reviewer. Stop when acceptance criteria are met.

### Example Prompt — Step 1: Re-establish Context

```
Read the applicable AGENTS.md and the documentation needed for your assigned task. Inspect affected code and its contracts. For a shared swarm, register with Agent Mail and check ownership before editing.
```

### Example Prompt — Step 2: Review Beads

```
We recently transformed a markdown plan file into a bunch of new beads. I want you to very carefully review and analyze these using `br` and `bv`.
```

### Example Prompt — Step 3: Polish

Then follow with the standard polish prompt.

---

## Test Coverage

### Example Prompt — Add Test Beads

```
Check whether the planned behaviors and material risks have appropriate verification. Identify missing checks and create task records only when authorized.
```

**Use when:** Feature beads exist but test coverage is unclear.

---

## Cross-Model Review Pattern

| Model | Role | Prompt |
|-------|------|--------|
| Available implementation model | Initial task graph | Plan to Beads (Full) |
| Available reviewer | Resolve material graph findings | Polish (Standard) |
| Independent reviewer, when authorized | Check unresolved risks | Fresh Session → Review |

---

## Prompt Usage Summary

| Stage | Prompt | Repetitions |
|-------|--------|-------------|
| Initial conversion | Plan to Beads | 1x |
| Polishing | Polish (Standard) | Until material findings are resolved |
| Unresolved finding | Fresh Session | Only when fresh context or expertise is needed |
| Test coverage | Add Test Beads | 1x |
| Final review | Review the remaining risks | Only when required or supported by new evidence |
