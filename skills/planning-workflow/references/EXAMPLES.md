# Planning Examples — Reference

## Table of Contents
- [Example Plan Documents](#example-plan-documents)
- [Example AGENTS.md Files](#example-agentsmd-files)
- [Best Practices Guides](#best-practices-guides)

---

## Example Plan Documents

| Project | Plan Link |
|---------|-----------|
| CASS Memory System | [PLAN_FOR_CASS_MEMORY_SYSTEM.md](https://github.com/Dicklesworthstone/cass_memory_system/blob/main/docs/planning/PLAN_FOR_CASS_MEMORY_SYSTEM.md) |
| CASS GitHub Pages Export | [PLAN_TO_CREATE_GH_PAGES_WEB_EXPORT_APP.md](https://github.com/Dicklesworthstone/coding_agent_session_search/blob/main/docs/planning/PLAN_TO_CREATE_GH_PAGES_WEB_EXPORT_APP.md) |

---

## Example AGENTS.md Files

| Project Type | Link |
|--------------|------|
| NextJS webapp + TypeScript CLI | [brenner_bot/AGENTS.md](https://github.com/Dicklesworthstone/brenner_bot/blob/main/AGENTS.md) |
| Bash script project | [repo_updater/AGENTS.md](https://github.com/Dicklesworthstone/repo_updater/blob/main/AGENTS.md) |

---

## Best Practices Guides

Keep best practices guides in your project folder and reference them in AGENTS.md:

- [claude_code_agent_farm/best_practices_guides](https://github.com/Dicklesworthstone/claude_code_agent_farm/tree/main/best_practices_guides)

When guidance is relevant to the assigned task, verify it against current primary
sources. Update project guidance only when changes are authorized.

---

## Recommended Tech Stacks

| Project Type | Stack |
|--------------|-------|
| **Web app** | TypeScript, Next.js 16, React 19, Tailwind, Supabase (performance-critical parts in Rust compiled to WASM) |
| **CLI tool** | Golang or Rust if very performance critical |

If a consequential library choice remains unresolved, research the specific
requirements using current primary sources. Select tools by the needed capability.
