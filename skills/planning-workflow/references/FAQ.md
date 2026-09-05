# Planning FAQ — Reference

## Table of Contents
- [Skeleton-First vs Planning](#skeleton-first-vs-planning)
- [Handling Unanticipated Problems](#handling-unanticipated-problems)
- [Task Division for Agents](#task-division-for-agents)
- [Agent Specialization](#agent-specialization)
- [Design Decisions Location](#design-decisions-location)

---

## Skeleton-First vs Planning

**Q: Shouldn't I code a skeleton first?**

A: Use a bounded prototype when it resolves a concrete uncertainty. Use a plan to capture scope, dependencies, decisions, and verification; split it when independent workstreams need separate context.

---

## Handling Unanticipated Problems

**Q: What about problems I didn't anticipate?**

A: Record assumptions and unresolved decisions. Revise when implementation provides new evidence. Review reduces uncertainty but cannot guarantee a plan will work; stop reviewing once the current acceptance criteria and material findings are resolved.

After implementing v1, you create another plan for v2. Nothing says you can only do one plan.

---

## Task Division for Agents

**Q: How do I divide tasks for agents?**

A: Each agent uses bv to find the next optimal bead and marks it in-progress. Distributed, robust, fungible agents.

---

## Agent Specialization

**Q: Do agents need specialization?**

A: Interchangeable agents help when their capabilities and permissions fit the tasks. Use specialized ownership for expertise, access restrictions, or independent review. A role name alone does not establish capability.

---

## Design Decisions Location

**Q: Should design decisions be in markdown or beads?**

A: The beads themselves can and should contain this markdown. You can have long descriptions/comments inside the beads—they don't need to be short bullet point type entries.
