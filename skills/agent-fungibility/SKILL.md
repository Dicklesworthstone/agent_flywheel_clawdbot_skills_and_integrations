---
name: agent-fungibility
description: "Compare interchangeable and specialized agents when designing multi-agent software workflows."
---

# Agent Fungibility — The Key to Scalable Agent Swarms

> **Core Principle:** "Fungibility bestows a LOT of really good properties automatically in a computer system."
>
> YOU are the bottleneck. Be the clockwork deity to your agent swarms: design a beautiful and intricate machine, set it running, and then move on to the next project.

---

## The Debate: Specialized vs. Fungible Agents

A burgeoning debate has sprung up around the optimal way to scale up the number of agents working on a software project:

| Approach | Description |
|----------|-------------|
| **Specialized Roles** | Assign distinct roles (tester agent, backend agent, committer agent, etc.) |
| **Fungible Agents** | Agents can replace each other within compatible assignments |

**Interchangeable agents can simplify recovery when tasks share the same capabilities and permissions.**

---

## Why Fungibility Works

### The Problem with Specialized Agents

Rather than setting up a complex heterogeneous system where you have assigned roles to specific tasks for agents, which is **brittle** and creates problems when one of the agents crashes or loses its memory or otherwise suffers from context rot and needs to be euthanized, you have to deal with:

1. **Understanding what kind of agent just died**
2. **What was it doing when it died**
3. **How to replace it functionally with the relevant context**
4. **What happens to the other agents that were depending on that specialized agent?**

### The Fungibility Solution

Use **fungible agents** for tasks whose tool access, context, and verification requirements they can all meet. Use specialized assignments when expertise, permissions, or independent review require them.

They can be any kind of agent:
- Claude Code
- Codex
- Antigravity CLI (`agy`, pinned to "Gemini 3.1 Pro (High)"; successor to the retiring Gemini CLI)
- Amp
- Cursor
- etc.

Treat agents as interchangeable only within assignments whose capabilities, permissions, and handoff requirements they each meet.

---

## The Two Big Unlocks

### 1. Use BV to Choose Optimal Next Bead

Within an explicitly assigned continuing queue, agents can use `bv --robot-triage` or `bv --robot-next` to propose the next ready bead. A proposal outside that queue is not a new assignment.

### 2. Put Everything in the Plan → Beads

If you put everything you want to have happening in your original markdown plan that you turn into beads, you get everything else "for free" and it's robust to bad things happening to any agents.

---

## Robustness Properties

Agents fail. They:
- Crash
- You accidentally close the tab
- Context rot (lose track of what they're doing)
- Get stuck in loops
- Need to be "euthanized" and restarted

**Interchangeable agents simplify replacement; handoff state and ownership still need verification.**

When an agent dies:
1. The bead it was working on remains marked in-progress
2. A capable replacement can pick it up after checking ownership
3. Transfer the current state, evidence, and remaining work
4. Release or hand off reservations held by the previous agent

---

## Scaling Properties

Add agents only when authorized, independent assignments can run concurrently.
Check each agent's capabilities, permissions, and file ownership before assignment.
Measure completed work and coordination costs before increasing the team size;
stop expanding when contention or review work outweighs the benefit.

---

## The Analogy: Fountain Codes

This is why I'm a huge fan of things like fountain codes (like RaptorQ) for file storage:

> Turn a file into an endless stream of fungible blobs with very little overhead and the user can catch any blob in any order and each new blob helps them reconstruct the file; there's no "rarest chunk" like with BitTorrent.

In software development:
- Each bead is a "blob"
- An agent can take a bead when it is assigned and the agent meets its requirements
- There's no "critical specialist" that becomes a bottleneck
- The system is resilient to partial failures

---

## When Specialized Roles DO Make Sense

There are contexts where designated roles for agents work better. Example: **Automated scientific inquiry** (like BrennerBot).

Why it works there:
- The discourse itself (the back and forth between different agent types) is the core mechanism of surfacing truth
- The debate structure IS the point

Tradeoffs to consider in software:
- In software development, we just want good code that works
- The goal is output, not discourse
- Fungibility removes bottlenecks and single points of failure

---

## The Clockwork Deity Philosophy

> **Most of my agent tooling and workflows are about removing me from the equation, because there's only one of me, but a potentially unlimited number of agents.**

The way to do this:
1. **Define the assignment**: Record scope, acceptance checks, and unresolved decisions; use additional review when a concrete concern warrants it.
2. **Structure authorized work**: Use beads when durable task tracking is requested or required, preserving the plan's dependencies.
3. **Coordinate within scope**: Use authorized agent communication and explicit file ownership.
4. **Bound execution**: Give each agent a stopping condition and inspect its verification evidence before accepting the result.

### Why This Works

It depends on checkable conditions:
- Each assigned model has the tools, permissions, and context its task needs.
- Review resolves a concrete uncertainty or tests an acceptance criterion.
- Decisions follow evidence rather than a fixed model ranking.
- Shared plans and handoffs preserve relevant context within available limits.

---

## Practical Implementation

### Starting a Fungible Swarm

```bash
# Spawn agents (any mix of types)
ntm spawn myproject --cc=3 --cod=2 --agy=1

# Give them all the SAME initial prompt
ntm send myproject --all "$(cat initial_prompt.txt)"
```

### The Initial Prompt (Same for All)

```
Read the applicable AGENTS.md and the documentation needed for your assigned task. Inspect affected code and its contracts. For a shared swarm, register with Agent Mail and check ownership before editing.

Be sure to check your agent mail and to promptly respond if needed to any messages; then proceed meticulously with your next assigned beads, working on the tasks systematically and meticulously and tracking your progress via beads and agent mail messages.

Don't get stuck in "communication purgatory" where nothing is getting done; be proactive about starting tasks that need to be done, but inform your fellow agents via messages when you do so and mark beads appropriately.

Choose ready work within the assigned scope using bv robot output. Check ownership, mark progress, and respond to relevant coordination messages. Once assigned work is complete, report the result and hand off remaining state.
```

### When an Agent Fails

1. Don't panic
2. Start a new session in its place
3. Give it the same initial prompt
4. It will:
   - Read AGENTS.md
   - Check bead status via bv
   - See what's in-progress/stuck
   - Either resume or pick a new bead

Verify replacement capabilities, ownership, and remaining acceptance criteria before resuming.

---

## Summary

| Property | Specialized Agents | Fungible Agents |
|----------|-------------------|-----------------|
| **Failure handling** | Find a matching specialist | Verify a capable replacement |
| **Scaling** | Check role capacity | Check independent assignments and contention |
| **Replacement** | Match the required specialty | Match capabilities and permissions |
| **Single point of failure** | Depends on available replacements | Depends on available replacements |
| **Coordination overhead** | Measure handoff costs | Measure ownership and review costs |
| **Human involvement** | Required for unresolved decisions | Required for unresolved decisions |

Interchangeable agents can simplify handoffs. Verify outcomes and retain the task's authorization limits.
