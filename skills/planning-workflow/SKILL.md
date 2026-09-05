---
name: planning-workflow
description: >-
  Comprehensive markdown planning methodology for software projects. Use when
  starting a new project, creating implementation plans, or refining architecture
  before coding.
---

<!-- TOC: Philosophy | THE EXACT PROMPT | Process Overview | References -->

# Planning Workflow — The Foundation of Agentic Development

> **Core Philosophy:** "Planning tokens are a lot fewer and cheaper than implementation tokens."
>
> Scale planning to uncertainty, dependencies, and risk. Keep the plan small enough to review and precise enough to implement.

---

## Outcome — When This Skill Has Delivered

You have a usable plan when **all** of the following hold:

- The plan is **self-contained**: a fresh agent who has never seen the project can read it and start implementing without asking the human for clarification.
- It is **dependency-aware**: every non-trivial task names what blocks it and what it unblocks, so the work decomposes cleanly into a beads graph.
- It is **justified**: every architectural choice and every non-obvious feature has at least one sentence on *why*, not just *what* — future agents need the rationale to make consistent local decisions.
- Review has resolved material gaps in scope, dependencies, and verification. Repeat a review only when new evidence or revisions warrant it.
- Each task has acceptance criteria. Convert to beads with the dependency graph intact when task creation is requested; a plan-only request ends with the reviewed plan.

Delivery requires clear scope, unresolved decisions called out, implementable tasks, and verification criteria. Length and review count are not acceptance criteria. Split a plan when independent workstreams need separate context.

## When NOT to Use This Skill

Reach for something else if:

- **The change is small and local** (one bug fix, one file, < ~200 LOC) → plan in chat or as a one-line TaskCreate; the planning overhead exceeds the implementation cost.
- **You are doing pure research** (investigating an unknown codebase, prototyping an idea) → use `codebase-archaeology` or `idea-wizard` first; planning is for execution, not discovery.
- **The architecture is dictated** (you are porting an existing system, following a spec, or implementing a well-defined RFC) → use `porting-to-rust` or `testing-conformance-harnesses`; the plan is the spec itself.
- **You're handling an incident or hotfix** → document the immediate hypothesis and verification, then expand the plan only if follow-up work needs it.

## Grounding — Sources of Truth for Plan Decisions

When a planning model proposes architecture, the proposal is a hypothesis. Ground every load-bearing claim in a verifiable source before letting it survive a review round:

- **Library/framework choices:** read the actual current docs (latest stable version, not the model's training-time snapshot). If the model says "use X for Y," verify X still exists, is maintained, and supports Y in the version you'd install.
- **Existing-codebase claims:** for any plan that touches an existing project, the model's understanding of the project structure is suspect. Grep, `git log`, or use `codebase-archaeology` to confirm structural claims before they shape the plan.
- **Performance / scaling claims:** never accept a number ("handles 10k req/s," "loads in <100ms") without a citation or a planned benchmark. Bare numbers in plans are guesses dressed as facts.
- **Cost claims:** verify against the provider's pricing page at planning time; pricing models change. Pin the plan to the specific tier you priced against.
- **Cross-references to other skills/tools:** if the plan says "use `<tool>` for X," confirm the tool's current contract supports X. Linkrot in plans is a quiet failure mode.

A plan that survived review without grounding is a plan that will surprise you in implementation. Cheap verification at planning time beats expensive rework after the code is half-written.

## Validation Loop (between review rounds)

Check these properties before delivering the plan:

1. **Self-containment check** — each task includes enough context and acceptance criteria to implement it.
2. **Dependency-graph check** — dependencies exist and have no cycles. Independent tasks and terminal tasks are valid.
3. **Justification check** — material architectural decisions explain their rationale and evidence.
4. **Revision check** — review material changes and unresolved findings; stop when these properties hold.

Resolve a failed check or report a blocked decision. Convert to beads only when requested.

---

## Why Planning Matters

- **Measure twice, cut once** — becomes "Check your plan N times, implement once"
- A very big, complex markdown plan is still shorter than a few substantive code files
- Front-loading human input in planning enables removing yourself from implementation
- The code will be written ridiculously quickly when you start enough agents with a solid plan

---

## Plan Review Prompt

```
Review this plan against the stated goals, constraints, dependencies, and acceptance criteria. Identify concrete defects or unresolved decisions, explain their impact, and propose scoped revisions. Keep additional feature ideas separate for approval.

<PASTE YOUR EXISTING COMPLETE PLAN HERE>
```

---

## Integrate Revisions

After reviewing the proposed changes, apply supported revisions within the requested planning scope:

```
Integrate supported, in-scope revisions into the plan. Explain any rejected change and identify decisions that still require input. Preserve the stated constraints and acceptance criteria.

```[Pasted text from GPT Pro]```
```

---

## Process Overview

Select available capabilities for the work;
steps 4–5 apply only when task creation is requested.

```
1. INITIAL PLAN
   └─► Explain goals, intent, workflows, tech stack

2. REFINE MATERIAL FINDINGS
   └─► Resolve material findings; repeat only when revisions need review

3. INDEPENDENT REVIEW (when uncertainty or risk justifies it)
   └─► Choose reviewers with relevant capabilities and sufficient context
   └─► Resolve disagreements against evidence and acceptance criteria

4. CONVERT TO BEADS (when task creation is requested)
   └─► Self-contained tasks with dependency structure

5. VALIDATE BEADS (when task creation is requested)
   └─► Verify dependencies, scope, and acceptance criteria
```

---

## What Makes a Great Plan

| Good Plan | Great Plan |
|-----------|------------|
| Describes what to build | Explains WHY you're building it |
| Lists features | Details user workflows and interactions |
| Mentions tech stack | Justifies tech choices with tradeoffs |
| Has tasks | Has tasks with dependencies and rationale |
| Lists tasks | Defines acceptance criteria and verification |

### Essential Elements

1. **Self-contained** — Never need to refer back to external docs
2. **Granular** — Break complex features into specific subtasks
3. **Dependency-aware** — What blocks what?
4. **Justified** — Include reasoning, not just instructions
5. **User-focused** — How does each piece serve the end user?

---

## Common Mistakes

1. **Starting before scope is clear** — Resolve decisions that block implementation
2. **Repeated review without new evidence** — Stop when acceptance criteria are met
3. **Choosing models by reputation alone** — Match available reasoning, tools, and context to the task
4. **One oversized plan** — Decompose independent workstreams when that improves review
5. **Losing context** — Convert plans to beads so agents don't need the original

---

## References

| Topic | Reference |
|-------|-----------|
| All exact prompts | [PROMPTS.md](references/PROMPTS.md) |
| Real-world examples | [EXAMPLES.md](references/EXAMPLES.md) |
| FAQ | [FAQ.md](references/FAQ.md) |
