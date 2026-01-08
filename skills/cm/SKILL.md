---
name: cm
description: "CASS Memory System - procedural memory for AI coding agents. Three-layer cognitive architecture with confidence decay, anti-pattern learning, and cross-agent knowledge transfer."
---

# CM - CASS Memory System

Procedural memory for AI coding agents. Transforms scattered sessions into persistent, cross-agent memory. Uses a three-layer cognitive architecture that mirrors human expertise development.

## Why This Exists

AI coding agents accumulate valuable knowledge but it's:
- **Trapped in sessions** - Context lost when session ends
- **Agent-specific** - Claude doesn't know what Cursor learned
- **Unstructured** - Raw logs aren't actionable guidance
- **Subject to collapse** - Naive summarization loses critical details

You've solved auth bugs three times this month across different agents. Each time you started from scratch.

CM solves this with cross-agent learning: a pattern discovered in Cursor is immediately available to Claude Code.

## Three-Layer Cognitive Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    EPISODIC MEMORY (cass)                           │
│   Raw session logs from all agents — the "ground truth"             │
└───────────────────────────┬─────────────────────────────────────────┘
                            │ cass search
                            ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    WORKING MEMORY (Diary)                           │
│   Structured session summaries: accomplishments, decisions, etc.    │
└───────────────────────────┬─────────────────────────────────────────┘
                            │ reflect + curate
                            ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    PROCEDURAL MEMORY (Playbook)                     │
│   Distilled rules with confidence tracking and decay                │
└─────────────────────────────────────────────────────────────────────┘
```

## The One Command You Need

```bash
cm context "<your task>" --json
```

**Run this before starting any non-trivial task.** Returns:
- **relevantBullets** - Rules from playbook scored by task relevance
- **antiPatterns** - Things that have caused problems
- **historySnippets** - Past sessions (yours and other agents')
- **suggestedCassQueries** - Deeper investigation searches

## Confidence Decay System

Rules aren't immortal. Confidence decays without revalidation:

| Mechanism | Effect |
|-----------|--------|
| **90-day half-life** | Confidence halves every 90 days without feedback |
| **4x harmful multiplier** | One mistake counts 4× as much as one success |
| **Maturity progression** | `candidate` → `established` → `proven` |

A rule helpful 8 times in January but never validated since loses confidence over time.

## Anti-Pattern Learning

Bad rules don't just get deleted. They become warnings:

```
"Cache auth tokens for performance"
    ↓ (3 harmful marks)
"PITFALL: Don't cache auth tokens without expiry validation"
```

When a rule is marked harmful multiple times, it's automatically inverted into an anti-pattern.

## ACE Pipeline (How Rules Are Created)

```
Generator → Reflector → Validator → Curator
```

| Stage | Role | LLM? |
|-------|------|------|
| **Generator** | Pre-task context hydration (`cm context`) | No |
| **Reflector** | Extract patterns from sessions (`cm reflect`) | Yes |
| **Validator** | Evidence gate against cass history | Yes |
| **Curator** | Deterministic delta merge | **No** |

**Critical:** Curator has NO LLM to prevent context collapse from iterative drift.

## Commands Reference

### Context Retrieval (Primary Workflow)

```bash
# THE MAIN COMMAND - run before non-trivial tasks
cm context "implement user authentication" --json

# Limit results for token budget
cm context "fix bug" --json --limit 5 --no-history

# Self-documenting explanation
cm quickstart --json

# System health
cm doctor --json
```

### Playbook Management

```bash
cm playbook list                              # All rules
cm playbook get b-8f3a2c                      # Rule details
cm playbook add "Always run tests first"      # Add rule
cm playbook add --file rules.json             # Batch add
cm playbook remove b-xyz --reason "Outdated"  # Remove
cm playbook export > backup.yaml              # Export
cm playbook import shared.yaml                # Import

cm top 10                                     # Top effective rules
cm stale --days 60                            # Rules without recent feedback
cm why b-8f3a2c                               # Rule provenance
cm stats --json                               # Playbook health metrics
```

### Learning & Feedback

```bash
# Manual feedback
cm mark b-8f3a2c --helpful
cm mark b-xyz789 --harmful --reason "Caused regression"
cm undo b-xyz789                              # Revert feedback

# Session outcomes (positional: status, rules)
cm outcome success b-8f3a2c,b-def456
cm outcome failure b-x7k9p1 --summary "Auth approach failed"
cm outcome-apply                              # Apply to playbook

# Reflection (usually automated)
cm reflect --days 7 --json

# Validation
cm validate "Always check null before dereferencing"

# Audit sessions against rules
cm audit --days 30

# Deprecate permanently
cm forget b-xyz789 --reason "Superseded by better pattern"
```

### Onboarding (Agent-Native)

Zero-cost playbook building using your existing agent:

```bash
cm onboard status                             # Check progress
cm onboard gaps                               # Category gaps
cm onboard sample --fill-gaps                 # Prioritized sessions
cm onboard read /path/session.jsonl --template  # Rich context
cm onboard mark-done /path/session.jsonl      # Mark processed
cm onboard reset                              # Start fresh
```

### Trauma Guard (Safety System)

```bash
cm trauma list                                # Active patterns
cm trauma add "DROP TABLE" --severity critical
cm trauma heal t-abc --reason "Intentional migration"
cm trauma remove t-abc
cm trauma scan --days 30                      # Scan for traumas
cm trauma import shared-traumas.yaml

cm guard --install                            # Claude Code hook
cm guard --git                                # Git pre-commit hook
cm guard --status                             # Check installation
```

### System Commands

```bash
cm init                                       # Initialize
cm init --starter typescript                  # With template
cm starters                                   # List templates
cm serve --port 3001                          # MCP server
cm usage                                      # LLM cost stats
cm privacy status                             # Privacy settings
cm privacy disable                            # Disable enrichment
cm project --format agents.md                 # Export for AGENTS.md
```

## Inline Feedback (During Work)

Leave feedback in code comments. Parsed during reflection:

```typescript
// [cass: helpful b-8f3a2c] - this rule saved me from a rabbit hole

// [cass: harmful b-x7k9p1] - this advice was wrong for our use case
```

## Agent Protocol

```
1. START:    cm context "<task>" --json
2. WORK:     Reference rule IDs when following them
3. FEEDBACK: Leave inline comments when rules help/hurt
4. END:      Just finish. Learning happens automatically.
```

You do NOT need to:
- Run `cm reflect` (automation handles this)
- Run `cm mark` manually (use inline comments)
- Manually add rules to the playbook

## Gap Analysis Categories

| Category | Keywords |
|----------|----------|
| `debugging` | error, fix, bug, trace, stack |
| `testing` | test, mock, assert, expect, jest |
| `architecture` | design, pattern, module, abstraction |
| `workflow` | task, CI/CD, deployment |
| `documentation` | comment, README, API doc |
| `integration` | API, HTTP, JSON, endpoint |
| `collaboration` | review, PR, team |
| `git` | branch, merge, commit |
| `security` | auth, token, encrypt, permission |
| `performance` | optimize, cache, profile |

Category status thresholds:
- `critical`: 0 rules (high priority)
- `underrepresented`: 1-2 rules
- `adequate`: 3-10 rules
- `well-covered`: 11+ rules

## Graceful Degradation

| Condition | Behavior |
|-----------|----------|
| No cass | Playbook-only scoring, no history snippets |
| No playbook | Empty playbook, commands still work |
| No LLM | Deterministic reflection, no semantic enhancement |
| Offline | Cached playbook + local diary |

## Output Format

All commands support `--json` for machine-readable output:

```json
{
  "success": true,
  "task": "fix the auth timeout bug",
  "relevantBullets": [
    {
      "id": "b-8f3a2c",
      "content": "Always check token expiry before auth debugging",
      "effectiveScore": 8.5,
      "maturity": "proven",
      "relevanceScore": 0.92
    }
  ],
  "antiPatterns": [...],
  "historySnippets": [...],
  "suggestedCassQueries": [...]
}
```

## Error Handling

```json
{
  "success": false,
  "code": "PLAYBOOK_NOT_FOUND",
  "error": "Playbook file not found",
  "hint": "Run 'cm init' to create a new playbook",
  "retryable": false
}
```

Exit codes:
- `1` internal error
- `2` user input/usage
- `3` configuration
- `4` filesystem
- `5` network
- `6` cass error
- `7` LLM/provider error

## Token Budget Management

| Flag | Effect |
|------|--------|
| `--limit N` | Cap number of rules |
| `--min-score N` | Only rules above threshold |
| `--no-history` | Skip historical snippets |
| `--json` | Structured output |

## Automating Reflection

Set up a cron job:

```bash
# Daily at 2am
0 2 * * * /usr/local/bin/cm reflect --days 7 >> ~/.cass-memory/reflect.log 2>&1
```

Or Claude Code post-session hook in `.claude/hooks.json`:
```json
{
  "post-session": ["cm reflect --days 1"]
}
```

## Integration with CASS

CASS provides **episodic memory** (raw sessions).
CM extracts **procedural memory** (rules and playbooks).

```bash
# CASS: Search raw sessions
cass search "authentication timeout" --robot

# CM: Get distilled rules for a task
cm context "authentication timeout" --json
```

## Data Locations

- Config: `~/.cass-memory/config.yaml`
- Playbook: `~/.cass-memory/playbook.yaml`
- Diary: `~/.cass-memory/diary/`
- Onboarding state: `~/.cass-memory/onboarding-state.json`

## Installation

```bash
curl -fsSL https://raw.githubusercontent.com/Dicklesworthstone/cass_memory_system/main/install.sh \
  | bash -s -- --easy-mode --verify
```
