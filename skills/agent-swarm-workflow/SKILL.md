---
name: agent-swarm-workflow
description: "Coordinate requested multi-agent implementation with NTM, Agent Mail, and Beads."
---

# Agent Swarm Workflow — Parallel Implementation

> **Core Insight:** Interchangeable agents simplify handoffs when their capabilities and permissions fit the assigned tasks. Match ownership and verification to the work, including independent review when needed.
>
> The swarm is distributed, robust, and self-organizing through Agent Mail and Beads.

---

## Prerequisites

Prompt templates below are adaptable examples within the requested swarm scope.
Use each harness's available reasoning controls; wording such as "ultrathink"
does not set a portable mode. Each agent needs an explicit task and ownership.

Before starting a swarm:

1. **Comprehensive plan** created (see `planning-workflow` skill)
2. **Polished beads** ready (see `beads-workflow` skill)
3. **AGENTS.md** provides local context and routes to relevant tool guidance
4. **Agent Mail server** running (`am` or `~/projects/mcp_agent_mail/scripts/run_server_with_token.sh`)
5. **NTM** available for session management

---

## The Swarm Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                         BEADS                               │
│     (Task graph with dependencies, priorities, status)      │
└─────────────────────────────────────────────────────────────┘
                              │
                    ┌─────────┴─────────┐
                    ▼                   ▼
┌─────────────────────────────┐  ┌─────────────────────────┐
│        BV                   │  │     AGENT MAIL          │
│  (What to work on)          │  │  (Coordination layer)   │
└─────────────────────────────┘  └─────────────────────────┘
         │                            │
         └──────────────┬─────────────┘
                        ▼
┌─────────────────────────────────────────────────────────────┐
│                    NTM + AGENTS                             │
│  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐     │
│  │ CC  │  │ CC  │  │ Cod │  │ Gmi │  │ CC  │  │ Cod │     │
│  └─────┘  └─────┘  └─────┘  └─────┘  └─────┘  └─────┘     │
└─────────────────────────────────────────────────────────────┘
```

---

## Starting the Swarm

### Using NTM (Named Tmux Manager)

```bash
# Spawn a swarm with multiple agents
ntm spawn myproject --cc=3 --cod=2 --agy=1

# Send initial prompt to all Claude Code agents
ntm send myproject --cc "$(cat initial_prompt.txt)"

# Or send to all agents
ntm send myproject --all "$(cat initial_prompt.txt)"
```

### Manual Setup

Create tmux sessions/panes for each agent in your project folder.

---

## Example Prompt — Initial Agent Marching Orders

Give each agent this EXACT prompt to start:

```
Read the applicable AGENTS.md and the documentation needed for your assigned task. Inspect affected code and its contracts. For a shared swarm, register with Agent Mail and check ownership before editing.

Be sure to check your agent mail and to promptly respond if needed to any messages; then proceed meticulously with your next assigned beads, working on the tasks systematically and meticulously and tracking your progress via beads and agent mail messages.

Don't get stuck in "communication purgatory" where nothing is getting done; be proactive about starting tasks that need to be done, but inform your fellow agents via messages when you do so and mark beads appropriately.

Choose ready work within the assigned scope using bv robot output. Check ownership, mark progress, and respond to relevant coordination messages. Once assigned work is complete, report the result and hand off remaining state.
```

---

## The Implementation Loop

### Example Prompt — Move to Next Bead

Once agents complete a bead, use this prompt to keep them moving:

```
Check applicable instructions if they changed. Use bv robot output to select ready work within the assigned scope, confirm ownership, and update task state. Finish when the assigned work and verification are complete.
```

### Example Prompt — Self-Review After Bead Completion

Have agents review their work before moving on:

```
Great, now I want you to carefully read over all of the new code you just wrote and other existing code you just modified with "fresh eyes" looking super carefully for any obvious bugs, errors, problems, issues, confusion, etc. Carefully fix anything you uncover.
```

**Stop when scoped findings are resolved and relevant checks pass. Repeat only after changes or new evidence.**

---

## Handling Context Compaction

### Example Prompt — Post-Compaction

When an agent does a compaction, immediately follow up with:

```
After compaction, recover applicable instructions, current task state, ownership, and remaining verification before continuing.
```

This re-establishes the critical context about tools and workflows.

---

## Quality Review Prompts

### Example Prompt — Cross-Agent Review

Periodically have agents review each other's work:

```
Review this task’s changes and affected callers. Report evidence. Fix confirmed defects within assigned ownership and scope; report unrelated findings for follow-up.
```

### Example Prompt — Random Code Exploration

For deep quality checks:

```
When broader exploration is requested, inspect code paths and dependencies within the requested area.

Report concrete findings and impact. Apply fixes only within requested scope and assigned file ownership.

Be sure to comply with ALL rules in AGENTS dot md and ensure that any code you write or revise conforms to the best practice guides referenced in the AGENTS dot md file.
```

---

## Committing Work

### Example Prompt — Commit Changes

Have agents commit logically grouped changes:

```
Inspect the diff and commit only changes owned by this task in logical groups. Preserve unrelated work. Verify the remote and follow repository landing policy; push only when the task authorizes publishing.
```

---

## Optional Follow-Up Prompts

Use these only for separately assigned follow-up work. Completing a bead does not authorize broader testing or UI changes.

### Example Prompt — Add Test Coverage

```
Check the requested behavior and material regression risks have appropriate unit or integration coverage. Add checks within scope; create follow-up tasks only when authorized.
```

### Example Prompt — UI/UX Scrutiny

```
Review the assigned interface and report concrete usability, accessibility, or visual defects against its acceptance criteria. Make changes only when authorized, verify affected desktop and mobile behavior, and stop when the assigned criteria are satisfied.
```

### Example Prompt — Deep UI/UX Enhancement

```
For the authorized UI improvement, inspect desktop and mobile separately. Fix observed problems within the assigned scope and verify the result. Return remaining concerns without expanding the assignment.
```

---

## Agent Mail Integration

### How Agents Coordinate

Each agent:
1. **Registers** with Agent Mail at session start
2. **Reserves files** before editing (`file_reservation_paths`)
3. **Announces work** via messages with bead ID in `thread_id`
4. **Checks inbox** between tasks
5. **Releases reservations** when done

### File Reservation Pattern

```python
# Before starting work on a bead
file_reservation_paths(
    project_key="/path/to/project",
    agent_name="GreenCastle",
    paths=["src/auth/**/*.ts"],
    ttl_seconds=3600,
    exclusive=True,
    reason="br-123"
)

# After completing work
release_file_reservations(project_key, agent_name)
```

### Communication Pattern

```python
# Announce starting a bead
send_message(
    project_key, agent_name,
    to=["BlueLake", "RedMountain"],  # Other active agents
    subject="[br-123] Starting auth module",
    body_md="I'm taking br-123. Reserved src/auth/**.",
    thread_id="br-123"
)

# Update on completion
send_message(
    project_key, agent_name,
    to=["BlueLake", "RedMountain"],
    subject="[br-123] Completed",
    body_md="Auth module done and tested. Released file reservations.",
    thread_id="br-123"
)
```

---

## Using BV for Task Selection

### Key Commands

```bash
# THE MEGA-COMMAND: Start here
bv --robot-triage

# Just get the single top pick
bv --robot-next

# Get parallel execution tracks (for multi-agent)
bv --robot-plan

# Check for cycles (MUST FIX if found)
bv --robot-insights | jq '.Cycles'

# Find bottlenecks
bv --robot-insights | jq '.bottlenecks'
```

**CRITICAL:** Never run bare `bv` — it launches interactive TUI that blocks the session.

---

## Quality Loops

### Run Until Clean

Choose the review appropriate to the changed area. Repeat only when a fix or new evidence requires another check:

1. **Self-review** — Agent reviews own code
2. **Cross-review** — Agent reviews other agents' code
3. **Broader exploration** — Only when requested, with a defined area and stopping point

### The Steady-State Signal

Finish when acceptance criteria and configured checks pass, scoped findings are resolved, and ownership and handoff state are clear. Report unrelated findings without expanding the task.

---

## Complete Prompt Reference

### Initial Marching Orders
```
Read the applicable AGENTS.md and the documentation needed for your assigned task. Inspect affected code and its contracts. For a shared swarm, register with Agent Mail and check ownership before editing.

Be sure to check your agent mail and to promptly respond if needed to any messages; then proceed meticulously with your next assigned beads, working on the tasks systematically and meticulously and tracking your progress via beads and agent mail messages.

Don't get stuck in "communication purgatory" where nothing is getting done; be proactive about starting tasks that need to be done, but inform your fellow agents via messages when you do so and mark beads appropriately.

Choose ready work within the assigned scope using bv robot output. Check ownership, mark progress, and respond to relevant coordination messages. Once assigned work is complete, report the result and hand off remaining state.
```

### Move to Next Bead
```
Check applicable instructions if they changed. Use bv robot output to select ready work within the assigned scope, confirm ownership, and update task state. Finish when the assigned work and verification are complete.
```

### Self-Review
```
Great, now I want you to carefully read over all of the new code you just wrote and other existing code you just modified with "fresh eyes" looking super carefully for any obvious bugs, errors, problems, issues, confusion, etc. Carefully fix anything you uncover.
```

### Cross-Review
```
Review this task’s changes and affected callers. Report evidence. Fix confirmed defects within assigned ownership and scope; report unrelated findings for follow-up.
```

### Random Exploration
```
When broader exploration is requested, inspect code paths and dependencies within the requested area.

Report concrete findings and impact. Apply fixes only within requested scope and assigned file ownership.

Be sure to comply with ALL rules in AGENTS dot md and ensure that any code you write or revises conforms to the best practice guides referenced in the AGENTS dot md file.
```

### Post-Compaction
```
After compaction, recover applicable instructions, current task state, ownership, and remaining verification before continuing.
```

### Commit Changes
```
Inspect the diff and commit only changes owned by this task in logical groups. Preserve unrelated work. Verify the remote and follow repository landing policy; push only when the task authorizes publishing.
```

### Test Coverage
```
Check the requested behavior and material regression risks have appropriate unit or integration coverage. Add checks within scope; create follow-up tasks only when authorized.
```

### UI/UX Scrutiny
```
Review the assigned interface and report concrete usability, accessibility, or visual defects against its acceptance criteria. Make changes only when authorized, verify affected desktop and mobile behavior, and stop when the assigned criteria are satisfied.
```

### Deep UI/UX Enhancement
```
For the authorized UI improvement, inspect desktop and mobile separately. Fix observed problems within the assigned scope and verify the result. Return remaining concerns without expanding the assignment.
```

---

## The Flywheel in Action

```
PLAN ──► BEADS ──► SWARM ──► REVIEW ──► COMMIT
  │                  │          │         │
  │                  │          └────┬────┘
  │                  │               │
  │                  └───── REPEAT ──┘
  │                              │
  │         v2 PLAN ◄────────────┘
  │              │
  └──────────────┘
```

Each cycle improves:
- **CASS** remembers solutions
- **CM** distills patterns
- **UBS** catches more issues
- **BV** shows graph health

---

## FAQ

**Q: How do agents know what to work on?**
A: They use `bv --robot-triage` or `bv --robot-next` to find the highest-impact ready bead.

**Q: How do they avoid conflicts?**
A: File reservations in Agent Mail. Exclusive reservations block others; the pre-commit guard enforces it.

**Q: What if an agent crashes or forgets?**
A: Every agent is fungible. Start a new session, read AGENTS.md, check bead status, continue.

**Q: How many agents should I run?**
A: Start with the smallest team that can perform the assigned independent work. Add an agent only when a bounded parallel task justifies the coordination cost.

**Q: What model mix works best?**
A: Choose available models by task requirements, tool access, and observed results. No fixed model mix is required.

**Q: Do agents need individual areas of expertise?**
A: Use interchangeable agents when their capabilities fit. Specialized ownership can help with permissions, expertise, or independent review.

**Q: Is there traceability between git commit and bead?**
A: Yes, bv automatically does this analysis and links beads to relevant git commits by analyzing the stream of data and making logical deductions.
