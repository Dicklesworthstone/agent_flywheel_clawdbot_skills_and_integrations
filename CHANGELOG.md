# Changelog

All notable changes to the Agent Flywheel Clawdbot Skills & Integrations collection.

This project has no versioned releases or tags. Changes are tracked by date and organized by capability area. Each entry links to the relevant commit on GitHub.

Repository: <https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations>

---

## 2026-03-14

### Skills — Binary Name Migration

- **Migrate `bd` references to `br` (beads_rust):** Updated all skill files that referenced the old `bd` binary to use `br`, the correct binary name for the Rust rewrite. Affected skills: agent-mail, agent-swarm-workflow, beads-workflow, bv, de-slopify, ntm, tanstack-integration, ui-ux-polish. ([`5127639`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/5127639ae17f37f0f55537d7a143287a727e0075))

---

## 2026-03-11

### Skills — Removed

- **Remove claude-chrome skill:** Deleted `skills/claude-chrome/SKILL.md` as part of a coordinated removal across repos. The Claude-in-Chrome browser automation skill is no longer maintained. ([`08a55b1`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/08a55b1c70edfacbfe4d7a1ff540fc938276cf3b))

---

## 2026-02-21 — 2026-02-22

### Licensing

- **Update license to MIT with OpenAI/Anthropic Rider:** Replaced the plain MIT license with a variant that restricts use by OpenAI, Anthropic, and their affiliates without express written permission from Jeffrey Emanuel. ([`f1b8c60`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/f1b8c60f6e44883940cd8f53c9997dfa32202885))
- **Update README license references:** README now reflects the MIT + OpenAI/Anthropic Rider license. ([`d77c953`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d77c9535ea412da36945ff36dee34a34bd71065f))

### Repository Housekeeping

- **Add GitHub social preview image:** Added a 1280x640 open-graph share image for consistent link previews. ([`2d382cf`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/2d382cfb25efea5d2e12d8f077a996451e7d82c8))

---

## 2026-02-15

### Repository Housekeeping

- **Add `.gitignore`:** Created `.gitignore` to exclude macOS `.DS_Store` files from tracking. ([`dffa00b`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/dffa00b3c6510041e8cd1a9ecd35d8b03c05fab3))

---

## 2026-01-29 — 2026-01-30

### Installer — New Capabilities

- **Add `~/.openclaw/skills` to path detection:** The installer now auto-detects OpenClaw's managed skills directory. Detection order: `~/clawd/skills` then `~/.openclaw/skills` then `~/.clawdbot/skills`. Closes #2. ([`35eeaee`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/35eeaeee79a0f5f9c097d9b125a25f35e6192b6c))

### Installer — Bug Fixes

- **Redirect log functions to stderr:** Log functions (`log_info`, `log_success`, `log_warn`, `log_step`) were writing to stdout, polluting output during command substitution captures and causing false "Skills directory not found" errors. All log functions now write to stderr. Fixes #1. ([`44ae2b9`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/44ae2b9e61c03921c7222cec043ec922046dda08))

---

## 2026-01-08

This was a major documentation day: 13 skills were comprehensively rewritten or created from scratch based on full README study of their upstream tools, the README was expanded with ACIP security and workflow methodology sections, and 9 new workflow/tool skills were added.

### Skills — Dicklesworthstone Stack (Comprehensive Rewrites)

Each of these rewrites transformed basic command references into exhaustive guides derived from studying the upstream tool's full README.

- **NTM (Named Tmux Manager):** Rewritten from 548 to 578 lines. Added "Why This Exists" section, installation methods, CASS integration, alerting system with severity levels, themes and display (5 color themes, agent-specific colors, responsive layout tiers), safety system for protected commands, work distribution with 4 assignment strategies, agent capability matrix, automatic compaction recovery, activity states, and pane naming conventions. ([`811d0dc`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/811d0dcce2702b54f858211ecf479a61c80e737e))

- **SLB (Simultaneous Launch Button):** Rewritten from 206 to 578 lines. Added client-side execution design, environment inheritance, complete command reference (session management, request/run, execution, pattern management, daemon/TUI, Claude Code hook, history/audit), pattern matching engine with classification algorithm and precedence rules, request lifecycle state machine, 5 security gates, dry-run pre-flight, rollback state capture, hierarchical configuration, agent event streaming (NDJSON), request attachments, emergency override with safeguards, outcome tracking, TUI dashboard layout, and exit codes. ([`7125b94`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7125b94a347e858f0bf27ab8798d58e540e3e881))

- **DCG (Destructive Command Guard):** Rewritten from 286 to 455 lines. Added whitelist-first architecture, fail-safe defaults, zero false negatives philosophy, explicit "What It ALLOWS" section, nuanced `git restore` handling, `--force-with-lease` as safe alternative, complete modular pack system (core, database, container, Kubernetes, cloud, infrastructure, system packs), environment variables, 4-stage processing pipeline diagram, CLI manual testing, edge cases, performance optimizations (SIMD, LazyLock, zero-copy), pattern counts, security threat model, and FAQ. ([`6f5faad`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/6f5faad948e1758a6befae5e2477199d125e49e5))

- **RU (Repo Updater):** Rewritten from 360 to 504 lines. Added AI-assisted review system (`ru review --plan/--apply`), agent-sweep for automated dirty repo processing, three-phase agent workflow, priority scoring algorithm for issue/PR triage, ntm integration with robot mode API, preflight checks and security guardrails (file denylist, secret scanning), XDG-compliant directory structure, layout modes, per-repo configuration, quality gates auto-detection, rate limiting with adaptive parallelism, exit codes for sync and agent-sweep, NDJSON results logging, troubleshooting guide, and architecture notes. ([`21f5c83`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/21f5c835407a35165ecf09694187743552a1e550))

- **Agent-Mail (MCP Agent Mail):** Rewritten with full feature coverage (expanded to 422 lines). Added Human Overseer, static exports, disaster recovery, contact policies table, message importance levels, Beads Viewer integration with robot flags, cross-project coordination, pre-commit guard with rename-aware and NUL-safe path handling, search syntax with boolean operators, Web UI features, static mailbox export (Ed25519 signing, Age encryption, scrub presets, deployment to GitHub/Cloudflare Pages), disaster recovery archives, mailbox health doctor commands, Docker deployment, and key environment variables. ([`1e91837`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/1e918372dfa89b8e10dd7cfa5b8c7142ba2602b4))

- **CM (CASS Memory System):** Expanded from 345 to 824 lines. Added history filtering by source, score decay visualization (90-day half-life), effective score formula, maturity state machine diagram, scientific validation section, expanded onboarding commands, 6 built-in starter playbooks (typescript, react, python, node, rust, general), MCP Server section (5 tools, 4 resources), complete configuration reference, environment variables table, data locations, privacy and security section with secret sanitization, performance characteristics, LLM cost estimates, batch rule addition, and expanded troubleshooting. ([`6352589`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/63525894e91ac58fdde34d4cffb4c8f34e991c44))

- **CASS (Coding Agent Session Search):** Expanded to 949 lines. Added aggregation and analytics (`--aggregate`, server-side counts), match highlighting, cursor-based pagination, query analysis/debugging (`--explain`, `--dry-run`), request correlation and idempotent operations, traceability (`--trace-file`), blended scoring formula with alpha values, 3-layer deduplication strategy, bookmark system, 9 saved view slots with keyboard shortcuts, density modes, 6 theme presets, role-aware styling, command palette, detail pane tabs, context window sizing with Peek Mode, API contract and versioning, flexible time input formats, and hash embedder fallback for semantic search. ([`fbfee83`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/fbfee837cd428134876bfaa80ffd2d9393b660e6))

- **BV (Beads Viewer):** Comprehensive rewrite. Added "Why BV vs raw beads.jsonl" comparison table, critical warning to never run bare `bv` (blocks agents), all 9 graph metrics with key insights, two-phase analysis pattern, complete robot commands reference, scoping/filtering flags, 8 built-in recipes, robot output JSON examples, jq quick reference, agent workflow template, all TUI views with keys, integration with `bd` CLI and Agent Mail, graph export formats, and time travel. ([`aed2838`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/aed2838d406871c7d9cc9bfe2e52533bffb2c5c3))

- **Agent-Mail (earlier rewrite):** Comprehensive rewrite based on full README study. Added problem statement, contact policies, all four macros, beads integration workflow, cross-project coordination, pre-commit guard, resource URIs, Web UI and Human Overseer, common pitfalls, and typical session pattern template. Removed redundant CLI examples to focus on MCP tools. ([`9831735`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/9831735f4c3e00262636ceb34f81136587691f1a))

- **CM (earlier rewrite):** Comprehensive rewrite. Added "Why CM exists" problem statement, three-layer cognitive architecture diagram, confidence decay (90-day half-life, 4x harmful multiplier), anti-pattern learning, ACE Pipeline (Generator, Reflector, Validator, Curator -- Curator has no LLM to prevent context collapse), inline feedback syntax, agent protocol lifecycle, onboarding commands, Trauma Guard, gap analysis categories, graceful degradation, exit codes, token budget flags, and automating reflection via cron/hooks. ([`42675ba`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/42675baa546d972e257dd595ab8316654b091a35))

- **CASS (earlier update):** Added search modes (lexical/semantic/hybrid with RRF formula), pipeline mode for chained searches, boolean operators (AND/OR/NOT/-), and remote sources setup wizard. ([`c7989b8`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/c7989b88c2fac91e4d79688008c14c2edee50561))

### Skills — New Tool Skills Created

- **UBS (Ultimate Bug Scanner):** New skill created from scratch. Covers why UBS exists, the golden rule (`ubs <changed-files> --fail-on-warning`), all 18 detection categories organized by severity, language-specific detection patterns for 8 languages, profiles (strict/loose), category packs, comparison mode, all output formats (text, json, jsonl, sarif, html), inline suppression syntax, exit codes, doctor command, agent integration hooks for 4+ AI coding tools, performance benchmarks, fix workflow pattern, custom AST rules, flywheel integration table, and troubleshooting. ([`9436928`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/94369282410b13383e537e5897d3b7d78e45cc98))

- **CAAM (Coding Agent Account Manager):** New skill created from scratch. Covers OAuth token file swapping with SHA-256 content hashing, vault profiles vs. isolated profiles, supported tools (Claude Code, Codex CLI, Gemini CLI) with auth locations, smart profile management (health scoring, rotation algorithms, cooldown tracking, automatic failover, project-profile associations), vault structure, workflow examples, installation methods, and FAQ. ([`e5fb06e`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/e5fb06e1e67b3b9d1bbac780ae6a97e38cf3eb02))
  - Then immediately expanded (394 to 522 lines) with "Why This Works" explanation, profile detection details, tool-specific auth details, activate/uninstall options, proactive token refresh, config file format, TUI dashboard (health indicators, cooldown display, hot reload, keybindings), parallel sessions setup, zero-friction mode, and additional FAQ. ([`d0abf59`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d0abf59aae9683cbebfd0fb0b096fdb049d2e820))

### Skills — Media & Documentation Tools (Comprehensive Rewrites)

- **GIIL (Get Image from Internet Link):** Rewritten from 256 to 460 lines. Added primary use case (remote AI debugging), problem table with solutions, four-tier capture strategy (download button, network interception, element screenshot, viewport screenshot), multi-platform support with URL patterns, complete command reference, output modes (file path, JSON, base64, URL-only), album mode with rate limiting and exponential backoff, image processing pipeline (EXIF extraction, HEIC/HEIF conversion, MozJPEG compression), download verification (content-type, magic bytes, HTML detection), exit codes with scripting examples, environment variables, performance timing, troubleshooting, and security guarantees. ([`0cac77a`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/0cac77a1428d805f5d15569c2b3eb82aab4b99ff))

- **CSCTF (Chat Shared Conversation To File):** Rewritten from 248 to 427 lines. Added design principles (determinism, minimal network, safety, clarity, atomicity), end-to-end workflow explanation per provider (Playwright stealth for ChatGPT/Gemini/Grok; Chrome session cookies/CDP for Claude), processing algorithms (provider-specific selectors with fallback chains, Turndown customization, normalization, slugging algorithm), complete command reference, output format details, GitHub Pages publishing (quick recipe, remembered settings, custom config), recipes (CI scrape, HTML-only, batch archive, custom cache), security and privacy analysis, performance timing, failure modes and remedies table, environment variables, comparison to copy/paste, and limitations. ([`388b822`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/388b8220962edaf00f023c041471027d71c4fca8))

### Skills — New Workflow Methodology Skills

Nine new workflow skills added in a single batch, along with updates to four existing tool skills:

- **planning-workflow:** 85%+ time on planning methodology with exact prompts for feature planning. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **beads-workflow:** Converting detailed plans into beads task structure. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **agent-swarm-workflow:** Multi-agent implementation workflow with marching orders. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **agent-fungibility:** Philosophy of interchangeable generalist agents. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **ui-ux-polish:** Iterative Stripe-level UI polish methodology with exact prompt. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **de-slopify:** Removing AI writing artifacts from documentation. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **tanstack-integration:** Strategic TanStack library adoption (avoid man-with-hammer). ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **dcg:** Initial Destructive Command Guard hook documentation. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))
- **flywheel-discord:** Discord community assistant security rules. ([`3db46df`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/3db46df14be001f180d7f0f78f9584f649bed951))

Updated in the same commit: agent-mail, bv, cm, and ru skills received initial workflow-methodology-aware updates.

### README & Documentation

- **Add ACIP security section to README:** Added prominent ACIP (Advanced Cognitive Inoculation Prompt) integration section with quick install command, documented all 7 new workflow methodology skills in the skills table, added DCG and RU to the Dicklesworthstone Stack, added flywheel-discord, updated `clawdbot.json` example with all 25 skills, added note that workflow skills are pure knowledge, and expanded Related Projects with ACIP, CM, DCG, RU links. ([`5044b11`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/5044b111a9593ff4af61bf4453dd615d8dcf5923))
- **De-slopify README (reverted):** Attempted to remove AI-speak artifacts ("intelligently", "instantly", "naturally") from README, then immediately reverted. ([`d746631`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d746631ac666ce7be4b35b0e8e6945b9b671aed0), reverted by [`25b5fc3`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/25b5fc35bf54ba69a250289baf8ebeb446e6612e))

---

## 2026-01-04 — 2026-01-05

### Initial Release

- **15 Clawdbot skills launched.** The initial commit established the repository with skills organized into three categories, plus a README, LICENSE (MIT), and basic installer script. ([`7a85393`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/7a8539321e36138202cd1ffc140d86ee38c5b6ce))

**Dicklesworthstone Stack (ACFS tools):**
  - `ntm` -- Named Tmux Manager for multi-agent orchestration
  - `agent-mail` -- MCP Agent Mail coordination layer
  - `bv` -- Beads Viewer task management TUI
  - `cass` -- Coding Agent Session Search
  - `cm` -- CASS Memory procedural memory system
  - `slb` -- Simultaneous Launch Button for dangerous commands

**Cloud & Infrastructure:**
  - `gcloud` -- Google Cloud Platform CLI
  - `wrangler` -- Cloudflare Workers/KV/R2/D1
  - `vercel` -- Vercel deployments
  - `supabase` -- Supabase DB/Edge Functions

**Development Tools:**
  - `github` -- GitHub CLI (gh)
  - `ssh` -- SSH patterns and utilities
  - `cursor` -- Cursor AI editor
  - `ghostty` -- Ghostty terminal
  - `wezterm` -- WezTerm terminal

### Skills — New Tool Skills Added (Day 1)

- **claude-chrome:** Browser automation via Claude in Chrome extension -- browser control, Chrome DevTools MCP (26 tools), workflow recording, scheduled tasks, multi-tab workflows, authenticated session support. (Later removed on 2026-03-11.) ([`fde831d`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/fde831dfa3f326eddcadf113265c56893c01aa00))
- **giil:** Get Image from Internet Link -- download full-resolution images from iCloud, Dropbox, Google Photos, and Google Drive share links for remote AI debugging. ([`e78e607`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/e78e6079d93a6d09e9170248b4f37d66cf7d2d46))
- **csctf:** Chat Shared Conversation To File -- convert ChatGPT, Gemini, Grok, and Claude share links to clean Markdown + HTML transcripts with preserved code fences. ([`d245d12`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d245d12c1d8228b922581e4d0eb9b0cd0beae28c))
- **ru:** Repo Updater -- 667 lines covering pre-flight checks, repository list management, sync operations, automation mode (JSON output, non-interactive, dry-run, resume), repo spec syntax, path layouts, parallel sync with flock coordination, conflict resolution, JSON output schema, exit codes, configuration reference, NDJSON logging, and troubleshooting. ([`4e5fd18`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/4e5fd18af5a15654603f34f88ffb1418533c9469))

### Skills — Day-1 Expansions

- **ntm:** Major expansion covering session creation, agent spawning, command palette, dashboard navigation, output capture and monitoring, context window management, Agent Mail integration, robot mode for AI automation, profiles/personas, notifications, command hooks, multi-agent coordination strategies, and shell aliases. ([`d36dacd`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/d36dacd0c8852f1c63201dbe1da21d3da97f3be0))
- **bv:** Expanded from 202 to 692 lines. Added critical "never run bare bv" warning, deep dive on all 9 graph-theoretic metrics (PageRank, betweenness, HITS, degree/closeness/eigenvector centrality, clustering coefficient, core number), two-phase analysis pattern, robot mode JSON schemas, recipe system, 15+ jq patterns, git correlation, time-travel, and diff output mode. ([`de46267`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/de462677626644550f4e525b65dc7cf789c6f0f2))
- **agent-mail:** Expanded from 188 to 509 lines. Added project identity rules, agent naming conventions, session lifecycle, complete MCP tools reference (17 tools), MCP resources reference (4 URIs), session patterns, cross-project coordination, file reservation system, pre-commit guard, message best practices, and ready-to-paste AGENTS.md blurb. ([`6e57f30`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/6e57f3079f740701ec46b20f510ef9da8c9f35a4))
- **cm:** Expanded from 157 to 414 lines. Added three-layer cognitive architecture (Episodic, Working, Procedural memory), confidence decay mechanics, anti-pattern learning, cross-agent learning, scientific validation workflow, outcome tracking, session lifecycle commands, maintenance commands, gap analysis, JSON output examples, and agent-optimized troubleshooting. ([`dd8458c`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/dd8458c59d7edd72cee713def35e75d4ad83fc19))

### Installer

- **Add curl one-liner installer:** Interactive menu-driven installer with `--all` flag for batch install, `gum` or bash fallback for UI, cache-busted URL, auto-detection of skills directory (`~/clawd/skills` or `~/.clawdbot/skills`), `--list`, `--uninstall`, `--dest`, generated `clawdbot.json` config snippet, and Catppuccin-inspired styling. ([`1e834fa`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/1e834fa23c9ed09a8f444cbbeca5f0c88b89a888))
- **Fix stdout/stderr handling for interactive mode:** Redirected menu output to stderr in `select_skills_gum`/`select_skills_bash`, read user input from `/dev/tty` in bash fallback, used safe arithmetic `$((var + 1))` instead of `((var++))`, and used global `INSTALLED_COUNT` to avoid stdout capture issues. Also expanded cass skill with comprehensive robot mode docs. ([`a641356`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/a64135600f353297ea0aa2da393b228c52040db9))

### Bug Fixes

- **Correct Clawdbot attribution:** Fixed incorrect attribution and GitHub URLs in README -- Clawdbot is by Peter Steinberger (steipete), not Anthropic. ([`cdb540a`](https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/commit/cdb540a3d5483a1a270d3353f869f38a8df8764b))

---

## Summary of Current Skill Inventory

**Dicklesworthstone Stack (8 skills):** ntm, agent-mail, bv, cass, cm, slb, dcg, ru

**Workflow Methodologies (7 skills):** planning-workflow, beads-workflow, agent-swarm-workflow, agent-fungibility, ui-ux-polish, de-slopify, tanstack-integration

**Cloud & Infrastructure (4 skills):** gcloud, wrangler, vercel, supabase

**Media & Image Tools (1 skill):** giil

**Documentation & Export (1 skill):** csctf

**Development Tools (5 skills):** github, ssh, cursor, ghostty, wezterm

**Discord Integration (1 skill):** flywheel-discord

**Additional Tool Skills (2 skills):** caam, ubs

**Total: 29 active skills** (claude-chrome was added then removed)
