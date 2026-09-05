---
name: beads-workflow
description: >-
  Convert markdown plans into beads with dependencies using br CLI. Use when
  creating task graphs, polishing beads before implementation, or bridging
  planning to agent swarm execution.
---

<!-- TOC: Quick Start | Example Prompt | Polishing | br Commands | bd → br Migration | Quality Checklist | Troubleshooting | References -->

# Beads Workflow — From Plan to Actionable Tasks

> Define implementable tasks with observable acceptance criteria and correct dependencies. Review until material findings are resolved; further passes require new evidence.

## Quick Start

```bash
# 1. Initialize beads in project
br init

# 2. Convert plan to beads (see Example Prompt below)

# 3. Polish iteratively
# Review scope, acceptance criteria, and dependency correctness

# 4. Validate
br dep cycles        # Must be empty
bv --robot-insights  # Check graph health

# 5. Begin implementation
bv --robot-next      # Get first bead
```

---

## Example Prompt — Plan to Beads Conversion

```
Convert the accepted plan into bounded tasks with acceptance criteria, dependencies, ownership, and the rationale needed for implementation. Preserve the agreed scope. Use the repository's supported issue tool and safe-write protocol only when issue creation is authorized.
```

### Shorter Version

```
Convert the accepted plan into scoped tasks with acceptance criteria and dependencies using the repository's authorized issue workflow.
```

### What This Creates

- Tasks and subtasks with clear scope
- Dependency links (what blocks what)
- Detailed descriptions with background, reasoning, considerations
- Self-contained (never need to consult original plan)

---

## Polishing Beads

### Example Prompt — Polish (Standard)

```
Review the assigned plan and its task graph against the requested scope, dependencies, and acceptance criteria. Report concrete omissions or conflicts. Revise records only when edits are authorized; keep additional ideas separate.

DO NOT OVERSIMPLIFY THINGS! DO NOT LOSE ANY FEATURES OR FUNCTIONALITY!

Include verification appropriate to the planned behavior and material regression risks. Preserve the plan's required outcomes without adding unrelated test work.
```

### Polishing Protocol

1. Run polish prompt
2. Review changes
3. Repeat only when revisions leave material findings to resolve
4. Stop when acceptance criteria are met and no material findings remain
5. If a specific unresolved finding needs fresh context or expertise, request a capable reviewer

---

## Fresh Session Technique

When an unresolved finding requires a fresh session, transfer its evidence and scope:

### Example Prompt — Re-establish Context

```
Read the applicable AGENTS.md and the documentation needed for your assigned task. Inspect affected code and its contracts. For a shared swarm, register with Agent Mail and check ownership before editing.
```

### Example Prompt — Then Review Beads

```
We recently transformed a markdown plan file into a bunch of new beads. I want you to very carefully review and analyze these using `br` and `bv`.
```

Then follow up with the standard polish prompt.

---

## br Commands

### Issue Lifecycle

```bash
br init                              # Initialize workspace
br create "Title" -t feature -p 1    # Create bead
br update <id> --status in_progress
br close <id> --reason "Done"
br reopen <id>                       # If needed
```

### Dependencies

```bash
br dep add br-child br-parent        # child depends on parent
br dep remove br-child br-parent
br dep list <id>
br dep tree <id>
br dep cycles                        # MUST be empty!
```

### Querying

```bash
br list                              # All beads
br ready                             # Actionable (not blocked)
br blocked                           # Blocked beads
br search "authentication"
br list --json                       # Machine-readable
```

### Sync to Git

```bash
br sync --flush-only                 # Only after authorized issue writes
# Inspect the export and follow the repository's safe ledger-write protocol.
# Stage only the intended records/files when commit and delivery are authorized.
```

---

## bd → br Migration (Docs)

Use this only for a requested migration to `br`. Existing `bd` references alone do not justify migration.

**Check the installed implementation first:**
- `bd` may be upstream Beads or a compatibility shim for `br`; inspect the repository's tool contract before changing commands.
- `br sync` never runs Git commands. Review any intentional export and commit or push only within authorized delivery work.

**Transform checklist (order matters):**
1. Confirm migration is authorized and inspect each command's supported `br` equivalent. Preserve `bd` commands when the repository still uses upstream Beads or its compatibility shim.
2. For an authorized migration, map export commands to `br sync --flush-only`; keep staging, commits, and pushes in the repository's separately scoped delivery workflow.
3. Do NOT assume issue IDs must change `bd-*` → `br-*` — the prefix is configurable (often remains `bd-*`).
4. Update daemon/auto-commit references only where the verified implementation no longer supports them

**Verify the intended migration scope:**
```bash
rg -n '`bd |bd sync|br sync' file.md  # Review each match against the repository's tool contract
```

---

## BV Robot Mode

**CRITICAL:** Never run bare `bv` — it launches interactive TUI.

```bash
bv --robot-triage                    # Full triage
bv --robot-next                      # Single top pick
bv --robot-plan                      # Parallel execution tracks
bv --robot-insights | jq '.Cycles'   # Check for cycles
bv --robot-insights | jq '.bottlenecks'
```

---

## Quality Checklist

Before implementation, verify each bead:

- [ ] **Self-contained** — Understandable without external context
- [ ] **Clear scope** — One coherent piece of work
- [ ] **Dependencies explicit** — Links to blocking/blocked beads
- [ ] **Testable** — Clear success criteria
- [ ] **Includes tests** — Unit and e2e tests in scope
- [ ] **Preserves features** — Nothing from plan was lost
- [ ] **Not oversimplified** — Complexity preserved where needed
- [ ] **No cycles** — `br dep cycles` returns empty

---

## Integration with Agent Mail

Use bead ID as the coordination thread:

```python
# Reserve files for bead
file_reservation_paths(..., reason="br-123")

# Announce work in thread
send_message(..., thread_id="br-123", subject="[br-123] Starting...")

# Close bead when done
br close br-123 --reason "Completed"
release_file_reservations(...)
```

---

## When Beads Are Ready

Your beads are ready for implementation when:

1. **Acceptance criteria met** — Tasks are implementable and material findings resolved
2. **Review requirements met**: Complete the review needed for the task's risks; a particular model or minimum number of reviewers is not required.
3. **No cycles** — `br dep cycles` returns empty
4. **Tests included** — Each feature has associated test beads
5. **Dependencies clean** — Graph makes logical sense

---

## References

| Topic | Reference |
|-------|-----------|
| All prompts | [PROMPTS.md](references/PROMPTS.md) |
| Bead structure | [BEAD-ANATOMY.md](references/BEAD-ANATOMY.md) |
| Troubleshooting | [TROUBLESHOOTING.md](references/TROUBLESHOOTING.md) |
| br command reference | See br --help or beads_rust README |
| BV integration | See bv-graph-triage skill |

---

## Troubleshooting

### Worktree Error Fix

If you get `failed to create worktree: 'main' is already checked out`, inspect the
installed implementation and repository sync configuration first. Only when its
documented workflow requires a dedicated sync branch and configuration changes
and publication are authorized, adapt this example to verified branch names:

```bash
git branch beads-sync main             # Only if this branch does not already exist
git remote -v                         # Verify the intended remote
git push -u origin beads-sync:refs/heads/beads-sync
# Configure the actual sync caller using its verified tool contract.
```

Use a dedicated sync branch only when required by the installed tool's contract.

### Quick Health Check

```bash
br config list        # All settings
br dep cycles         # Must be empty
which br              # Verify br is installed
```

See [TROUBLESHOOTING.md](references/TROUBLESHOOTING.md) for full diagnostics.

---

## Validation

```bash
# Check for cycles (must be empty)
br dep cycles

# Check graph health
bv --robot-insights | jq '.Cycles'

# Verify all beads have descriptions
br list --json | jq '.issues[]? | select(.description == "")'
```
