# Planning Prompts — Complete Reference

## Table of Contents
- [Plan Review](#plan-review)
- [Integrate Revisions](#integrate-revisions)
- [Compare Plans](#compare-plans)
- [Initial Plan Creation](#initial-plan-creation)

---

## Plan Review

Use an available reasoning model suited to the plan. Include the relevant plan and its acceptance criteria:

```
Review this plan against the stated goals, constraints, dependencies, and acceptance criteria. Identify concrete defects or unresolved decisions, explain their impact, and propose scoped revisions. Keep additional feature ideas separate for approval.

<PASTE YOUR EXISTING COMPLETE PLAN HERE>
```

---

## Integrate Revisions

After reviewing the proposed changes, apply supported revisions within the requested planning scope:

```
Integrate supported, in-scope revisions into the plan. Explain any rejected change and identify decisions that still require input. Preserve the stated constraints and acceptance criteria.

[Paste reviewed revisions here]
```

### Review Completion

- Review scope, dependencies, decisions, and acceptance criteria.
- Repeat when a revision or new evidence needs review.
- Finish when material findings are resolved; there is no minimum round count.

---

## Compare Plans

When another perspective is useful, compare supplied plans against evidence and the requested outcome:

```
Compare the supplied plans against the requested outcome and available evidence. Integrate supported corrections that fit the agreed scope. Explain rejected alternatives and unresolved decisions. Provide focused diffs; neither a longer plan nor inclusion of every suggestion is required.

[Paste competing plans here]
```

---

## Initial Plan Creation

When starting a new project, include:

1. **Goals and Intent** — What you're really trying to accomplish
2. **Workflows** — How the final software should work from the user's perspective
3. **Tech Stack** — Be specific (e.g., "TypeScript, Next.js 16, React 19, Tailwind, Supabase")
4. **Architecture Decisions** — High-level structure and patterns
5. **The "Why"** — The more the model understands your end goal, the better it performs

An available agent can draft the plan from the stated goals and constraints; verify its assumptions before accepting the result.
