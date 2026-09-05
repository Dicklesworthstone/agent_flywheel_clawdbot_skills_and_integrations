# Beads Troubleshooting — Reference

## Table of Contents
- [Worktree Errors](#worktree-errors)
- [Sync Issues](#sync-issues)
- [br vs bd Migration](#br-vs-bd-migration)
- [Common Problems](#common-problems)

---

## Worktree Errors

### The Problem

```
Error pulling from sync branch: failed to create worktree: exit status 128
fatal: 'main' is already checked out at '/path/to/repo'
```

Some Beads implementations use Git worktrees for sync operations. Inspect the
installed tool and repository configuration before applying a fix. `br sync`
does not run Git commands, so trace this error to the actual caller.

### The Fix

Only when the installed tool requires a dedicated sync branch and configuration
changes and publication are authorized, adapt this example to verified names:

```bash
git branch beads-sync main  # Only if the branch does not already exist
git remote -v              # Verify the intended remote
git push -u origin beads-sync:refs/heads/beads-sync
# Set the sync branch using the installed tool's documented configuration command.
```

### For New Projects

Initialize issue storage only when requested. Follow the repository's installed
tool contract; do not add a sync branch unless that implementation needs one.

---

## Sync Issues

### Sync Commands

| Command | What it does |
|:--------|:-------------|
| `br sync --flush-only` | Export to JSONL only (no git operations) |
| `br sync` | Local synchronization; inspect `br sync --help` for modes; no Git operations |

### Check Sync Branch Configuration

```bash
br config list                     # Inspect supported configuration
git branch                         # Inspect branches if the workflow uses one
git ls-remote --heads origin beads-sync  # Verify on remote
```

---

## br vs bd Migration

The repository may use upstream `bd`, `br`, or a `bd` compatibility shim.
Detect the implementation first. These are candidate equivalents for an
authorized migration, not instructions to replace every `bd` reference:

| Old (bd) | New (br) | Notes |
|:---------|:---------|:------|
| `bd init` | `br init` | Check storage format and options |
| `bd create "Title"` | `br create "Title"` | Check required fields and flags |
| `bd sync` | Inspect `br sync --help` | Git delivery remains separate |
| `bd sync --flush-only` | `br sync --flush-only` | Verify export path and safe-write procedure |
| `bd list` | `br list` | Check filters and output format |
| `bd config` | `br config` | Inspect supported keys |

### If you have both installed

Use the implementation selected by the repository; inspect rather than change PATH:

```bash
command -v bd br
br --version
```

---

## Common Problems

| Problem | Diagnosis | Fix |
|:--------|:----------|:----|
| Worktree errors | Inspect caller and installed sync implementation | Apply its documented fix only when changes are authorized |
| Sync branch missing | Inspect the workflow's configured branch | Publish only if required and authorized, using an explicit refspec |
| br not found | `command -v br` returns nothing | Check repository requirements before an authorized installation |
| Cycles in graph | `br dep cycles` not empty | Report conflicting dependencies; edit records only when authorized |
| bv shows nothing | No beads created | Run `br list` to verify |

### Health Check

```bash
br config list        # All settings
br dep cycles         # Must be empty
bv --robot-insights   # Check graph health
```

---

## Configuration Reference

```bash
br config list                              # Show all settings
br config --help                            # Inspect supported keys and commands
# Change configuration only within authorized setup or repair work.
```
