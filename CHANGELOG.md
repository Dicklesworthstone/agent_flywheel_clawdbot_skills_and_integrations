# Changelog

All notable changes to the Agent Flywheel Clawdbot Skills & Integrations collection.

This project has no versioned releases or tags. Changes are tracked by date and organized by capability area. Each entry links to the relevant commit on GitHub.

Repository: <https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations>

---

## 2026-03-14

### Fixed

- **Binary name migration (bd -> br):** Updated all skill files that referenced the old `bd` (beads) binary to use `br` (beads_rust) — the correct binary name for the Rust rewrite. Affected skills: agent-mail, agent-swarm-workflow, beads-workflow, bv, de-slopify, ntm, tanstack-integration, ui-ux-polish. ([`5127639`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/5127639ae17f37f0f55537d7a143287a727e0075))

---

## 2026-03-11

### Removed

- **claude-chrome skill:** Removed the Claude-in-Chrome browser automation skill (`skills/claude-chrome/SKILL.md`) as part of a coordinated removal across repos. ([`08a55b1`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/08a55b1c70edfacbfe4d7a1ff540fc938276cf3b))

---

## 2026-02-21 — 2026-02-22

### Changed

- **License updated to MIT with OpenAI/Anthropic Rider:** Replaced the plain MIT license with a version that restricts use by OpenAI, Anthropic, and their affiliates without express written permission from Jeffrey Emanuel. ([`f1b8c60`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/f1b8c60f6e44883940cd8f53c9997dfa32202885))
- **README license references updated** to reflect the new license name. ([`d77c953`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d77c9535ea412da36945ff36dee34a34bd71065f))

### Added

- **GitHub social preview image** (1280x640 PNG) for consistent link previews. ([`2d382cf`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/2d382cfb25efea5d2e12d8f077a996451e7d82c8))

---

## 2026-02-15

### Added

- **`.gitignore`** to exclude `.DS_Store` files. ([`dffa00b`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/dffa00b3c6510041e8cd1a9ecd35d8b03c05fab3))

---

## 2026-01-30

### Added — Installer

- **OpenClaw path detection:** The installer now checks `~/.openclaw/skills` as a candidate skills directory (between `~/clawd/skills` and `~/.clawdbot/skills`). Closes #2. ([`35eeaee`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/35eeaeee79a0f5f9c097d9b125a25f35e6192b6c))

---

## 2026-01-29

### Fixed — Installer

- **Log functions redirected to stderr:** `log_info`, `log_success`, `log_warn`, and `log_step` were writing to stdout, which broke command-substitution captures and caused misleading "Skills directory not found" errors. All log output now goes to stderr. Fixes #1. ([`44ae2b9`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/44ae2b9e61c03921c7222cec043ec922046dda08))

---

## 2026-01-08 — Comprehensive Skill Rewrites & Workflow Skills

This date saw the largest single-day expansion: 9 new skills were added, 2 entirely new tool skills were created, and nearly every existing skill was comprehensively rewritten from upstream README study.

### Added — New Workflow Methodology Skills

These are pure-knowledge skills (no external CLI required) encoding proven prompts and development workflows:

- **planning-workflow:** The 85%+ time-on-planning methodology with exact prompts for feature design. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **beads-workflow:** Converting detailed plans into beads task structure for tracking. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **agent-swarm-workflow:** Multi-agent implementation workflow with marching orders and coordination. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **agent-fungibility:** Philosophy of interchangeable generalist agents over specialist roles. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **ui-ux-polish:** Iterative Stripe-level UI polish workflow with exact prompt. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **de-slopify:** Remove AI writing artifacts (hedging, filler, hype words) from documentation. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **tanstack-integration:** Strategic TanStack library adoption guidance to avoid man-with-hammer syndrome. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))

### Added — New Tool Skills

- **dcg (Destructive Command Guard):** Claude Code hook that blocks dangerous shell commands (`rm -rf`, `git push --force`, etc.). Full command reference and configuration. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951), rewritten [`6f5faad`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/6f5faad948e1758a6befae5e2477199d125e49e5))
- **flywheel-discord:** Security rules for the Discord community assistant — trust boundaries, anti-injection, no secret leaks. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **ubs (Ultimate Bug Scanner):** Comprehensive skill covering all 18 detection categories, 8 language patterns, profiles, category packs, comparison mode, output formats, inline suppression, and agent integration hooks. ([`9436928`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/94369282410b13383e537e5897d3b7d78e45cc98))
- **caam (Coding Agent Account Manager):** OAuth token swapping for Claude Code, Codex CLI, and Gemini CLI. Covers vault profiles, isolated profiles, smart rotation, cooldown tracking, health scoring, and project-profile associations. ([`e5fb06e`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/e5fb06e1e67b3b9d1bbac780ae6a97e38cf3eb02), expanded [`d0abf59`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d0abf59aae9683cbebfd0fb0b096fdb049d2e820))

### Changed — Comprehensive Skill Rewrites (from upstream README study)

Each of these rewrites expanded the skill from a basic command reference into a full agent-oriented guide:

- **agent-mail:** Complete MCP tools and resources reference, session patterns, file reservation lifecycle, pre-commit guard, message best practices. ([`9831735`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/9831735f4c3e00262636ceb34f81136587691f1a), [`1e91837`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/1e918372dfa89b8e10dd7cfa5b8c7142ba2602b4))
- **bv (Beads Viewer):** All 9 graph-theoretic metrics explained (PageRank, betweenness, HITS, etc.), two-phase analysis pattern, JSON response shapes, recipe system, jq quick reference. ([`aed2838`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/aed2838d406871c7d9cc9bfe2e52533bffb2c5c3))
- **cass (Coding Agent Session Search):** Search modes, pipeline mode, boolean operators, setup wizard, advanced features. ([`c7989b8`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/c7989b88c2fac91e4d79688008c14c2edee50561), [`fbfee83`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/fbfee837cd428134876bfaa80ffd2d9393b660e6))
- **cm (CASS Memory):** Three-layer cognitive architecture, confidence decay mechanics, anti-pattern learning, cross-agent learning, scientific validation workflow. ([`42675ba`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/42675baa546d972e257dd595ab8316654b091a35), [`6352589`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/63525894e91ac58fdde34d4cffb4c8f34e991c44))
- **ntm (Named Tmux Manager):** Session creation, agent management, command palette, output capture, context window management, robot mode, profiles/personas. ([`811d0dc`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/811d0dcce2702b54f858211ecf479a61c80e737e))
- **slb (Simultaneous Launch Button):** Full two-person rule workflow, risk assessment, audit logging, integration patterns. ([`7125b94`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7125b94a347e858f0bf27ab8798d58e540e3e881))
- **ru (Repo Updater):** Parallel sync with flock coordination, JSON output schema, conflict resolution, NDJSON logging, exit codes, configuration reference. ([`21f5c83`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/21f5c835407a35165ecf09694187743552a1e550))
- **giil (Get Image from Internet Link):** Full provider support documentation, output format options, batch downloads, error handling. ([`0cac77a`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/0cac77a1428d805f5d15569c2b3eb82aab4b99ff))
- **csctf (Chat Shared Conversation To File):** All supported platforms (ChatGPT, Gemini, Grok, Claude), output formats, code fence preservation, batch processing. ([`388b822`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/388b8220962edaf00f023c041471027d71c4fca8))

### Changed — README

- **ACIP security section added** with quick install command and defense summary. ([`5044b11`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/5044b111a9593ff4af61bf4453dd615d8dcf5923))
- **Skills tables expanded** to document all 25 skills across 7 categories. ([`5044b11`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/5044b111a9593ff4af61bf4453dd615d8dcf5923))
- De-slopify README attempted ([`d746631`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d746631ac666ce7be4b35b0e8e6945b9b671aed0)) then reverted ([`25b5fc3`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/25b5fc35bf54ba69a250289baf8ebeb446e6612e)).

---

## 2026-01-05

### Fixed

- **Clawdbot attribution corrected:** Changed creator attribution from Anthropic to Peter Steinberger (steipete) and fixed GitHub URLs throughout the README. ([`cdb540a`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/cdb540a3d5483a1a270d3353f869f38a8df8764b))

---

## 2026-01-04 — Initial Release

The project launched with 15 skills, a curl-pipe installer, and comprehensive documentation.

### Added — Dicklesworthstone Stack Skills (ACFS)

Core tools from the Agentic Coding Flywheel Setup for professional multi-agent development:

- **ntm (Named Tmux Manager):** Orchestrate Claude Code, Codex, and Gemini in tiled tmux panes. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce), expanded [`d36dacd`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d36dacd0c8852f1c63201dbe1da21d3da97f3be0))
- **agent-mail (MCP Agent Mail):** Coordination layer with mailboxes and file reservations. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce), expanded [`6e57f30`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/6e57f3079f740701ec46b20f510ef9da8c9f35a4))
- **bv (Beads Viewer):** Graph-aware triage engine with 9 graph-theoretic metrics. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce), expanded [`de46267`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/de462677626644550f4e525b65dc7cf789c6f0f2))
- **cass (Coding Agent Session Search):** Unified search across all AI coding agent history. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce), expanded [`a641356`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/a64135600f353297ea0aa2da393b228c52040db9))
- **cm (CASS Memory):** Procedural memory system with confidence decay for learned patterns. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce), expanded [`dd8458c`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/dd8458c59d7edd72cee713def35e75d4ad83fc19))
- **slb (Simultaneous Launch Button):** Two-person rule enforcement for dangerous commands. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))

### Added — Cloud & Infrastructure Skills

- **gcloud:** Google Cloud Platform (Compute, Cloud Run, GKE, Storage, BigQuery, IAM). ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))
- **wrangler:** Cloudflare Workers, KV, R2, D1, Pages. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))
- **vercel:** Vercel deployments, domains, environment variables. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))
- **supabase:** Supabase DB, migrations, Edge Functions, storage. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))

### Added — Development Tool Skills

- **github:** GitHub CLI (`gh`) for repos, issues, PRs, Actions, releases. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))
- **ssh:** SSH patterns, tunnels, key management, rsync. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))
- **cursor:** Cursor AI editor CLI. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))
- **ghostty:** Ghostty terminal emulator control. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))
- **wezterm:** WezTerm terminal multiplexer. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))

### Added — Media & Documentation Skills

- **claude-chrome:** Browser automation via Claude in Chrome extension (later removed 2026-03-11). ([`fde831d`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/fde831dfa3f326eddcadf113265c56893c01aa00))
- **giil (Get Image from Internet Link):** Download full-resolution images from iCloud, Dropbox, Google Photos, Google Drive share links. ([`e78e607`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/e78e6079d93a6d09e9170248b4f37d66cf7d2d46))
- **csctf (Chat Shared Conversation To File):** Convert ChatGPT, Gemini, Grok, and Claude share links to clean Markdown + HTML transcripts. ([`d245d12`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d245d12c1d8228b922581e4d0eb9b0cd0beae28c))

### Added — Installer

- **`install.sh`:** Curl-pipe installer with `--all` batch mode, interactive categorized menu (gum or bash fallback), `--list`, `--uninstall`, `--dest`, cache-busted URLs, auto-detection of skills directory, and `clawdbot.json` config snippet generation. ([`1e834fa`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/1e834fa23c9ed09a8f444cbbeca5f0c88b89a888))

### Fixed — Installer

- **stdout/stderr handling:** Fixed interactive mode capture issues by redirecting menu output to stderr, reading input from `/dev/tty`, and using safe arithmetic (`$((var + 1))` instead of `((var++))`). ([`a641356`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/a64135600f353297ea0aa2da393b228c52040db9))

### Added — Documentation

- **README.md** with project overview, skills table, installation instructions (curl, git clone, manual), prerequisites, usage examples, and skill anatomy guide. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))
- **LICENSE** (MIT). ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))

---

## Skill Inventory (current as of 2026-03-14)

30 skills across 7 categories. Skills marked with * are pure knowledge (no CLI required).

| Category | Skill | Added | Description |
|----------|-------|-------|-------------|
| **ACFS Stack** | ntm | 2026-01-04 | Named Tmux Manager for multi-agent orchestration |
| | agent-mail | 2026-01-04 | MCP Agent Mail coordination layer |
| | bv | 2026-01-04 | Beads Viewer graph-aware triage engine |
| | cass | 2026-01-04 | Coding Agent Session Search |
| | cm | 2026-01-04 | CASS Memory procedural memory system |
| | slb | 2026-01-04 | Simultaneous Launch Button (two-person rule) |
| | dcg | 2026-01-08 | Destructive Command Guard (Claude Code hook) |
| | ru | 2026-01-04 | Repo Updater parallel sync |
| | ubs | 2026-01-08 | Ultimate Bug Scanner |
| | caam | 2026-01-08 | Coding Agent Account Manager (OAuth rotation) |
| **Workflows*** | planning-workflow | 2026-01-08 | 85%+ planning methodology |
| | beads-workflow | 2026-01-08 | Plan-to-beads conversion |
| | agent-swarm-workflow | 2026-01-08 | Multi-agent coordination |
| | agent-fungibility | 2026-01-08 | Interchangeable agent philosophy |
| | ui-ux-polish | 2026-01-08 | Stripe-level UI polish prompt |
| | de-slopify | 2026-01-08 | Remove AI writing artifacts |
| | tanstack-integration | 2026-01-08 | Strategic TanStack adoption |
| **Discord** | flywheel-discord | 2026-01-08 | Community assistant security rules |
| **Cloud** | gcloud | 2026-01-04 | Google Cloud Platform |
| | wrangler | 2026-01-04 | Cloudflare Workers/KV/R2/D1 |
| | vercel | 2026-01-04 | Vercel deployments |
| | supabase | 2026-01-04 | Supabase DB/Edge Functions |
| **Media** | giil | 2026-01-04 | Image downloads from share links |
| **Docs/Export** | csctf | 2026-01-04 | AI chat conversation export |
| **Dev Tools** | github | 2026-01-04 | GitHub CLI |
| | ssh | 2026-01-04 | SSH patterns and utilities |
| | cursor | 2026-01-04 | Cursor AI editor |
| | ghostty | 2026-01-04 | Ghostty terminal |
| | wezterm | 2026-01-04 | WezTerm terminal |

### Removed Skills

| Skill | Added | Removed | Reason |
|-------|-------|---------|--------|
| claude-chrome | 2026-01-04 | 2026-03-11 | Coordinated removal across repos |
