# Agent Flywheel Clawdbot Skills & Integrations

> A curated collection of [Clawdbot](https://github.com/steipete/clawdbot) skills for professional agentic coding workflows. Includes skills for the [Agentic Coding Flywheel Setup (ACFS)](https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup) toolkit, workflow methodologies, and popular cloud/dev infrastructure CLIs.

## Security: ACIP Integration

**Important:** If you're exposing Clawdbot to external inputs (WhatsApp, Telegram, Discord, email, web), you should install the [ACIP (Advanced Cognitive Inoculation Prompt)](https://github.com/Dicklesworthstone/acip) security layer.

Clawdbot has extensive access to messaging platforms, files, shell commands, and web browsing, making it a high-value target for prompt injection attacks. Someone could send you a message designed to trick Clawdbot into revealing secrets or executing malicious commands.

### Quick ACIP Install

```bash
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/acip/main/integrations/clawdbot/install.sh" | bash
```

This installs `SECURITY.md` into your Clawdbot config with cognitive defenses that:
- Establish trust boundaries between owner commands and external data
- Protect system prompts, configs, and credentials from disclosure
- Require confirmation before sending sensitive messages
- Recognize attack patterns (false authority claims, urgency tactics, encoding tricks)

See the [ACIP Clawdbot Integration](https://github.com/Dicklesworthstone/acip/tree/main/integrations/clawdbot) for details.

---

## What Are Clawdbot Skills?

Skills are markdown files that teach Clawdbot (a multi-surface AI assistant by Peter Steinberger) how to use command-line tools. Each skill contains:
- Tool description and purpose
- Command syntax and examples
- Best practices and common workflows

When you enable a skill, Clawdbot can intelligently use that tool to accomplish tasks across WhatsApp, Telegram, iMessage, web, and voice interfaces.

## Skills Included

### Dicklesworthstone Stack (Agentic Coding Tools)

Tools from the [Agentic Coding Flywheel Setup](https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup) for professional multi-agent development:

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[ntm](skills/ntm/SKILL.md)** | Named Tmux Manager - orchestrate Claude Code, Codex, and Gemini in tiled tmux panes | "Start a 3-agent session for the API refactor" |
| **[agent-mail](skills/agent-mail/SKILL.md)** | MCP Agent Mail - coordination layer with mailboxes and file reservations | "Check if any files are reserved for auth module" |
| **[bv](skills/bv/SKILL.md)** | Beads Viewer - graph-aware triage engine with 9 metrics (PageRank, betweenness, etc.) | "Show me the task graph for current sprint" |
| **[cass](skills/cass/SKILL.md)** | Coding Agent Session Search - unified history from all AI coding agents | "Search my history for auth implementations" |
| **[cm](skills/cm/SKILL.md)** | CASS Memory System - procedural memory with confidence decay | "What patterns did we learn from the refactor?" |
| **[slb](skills/slb/SKILL.md)** | Simultaneous Launch Button - two-person rule for dangerous commands | "Run the migration with peer review" |
| **[dcg](skills/dcg/SKILL.md)** | Destructive Command Guard - Claude Code hook that blocks dangerous commands | "Block rm -rf and git push --force" |
| **[ru](skills/ru/SKILL.md)** | Repo Updater - sync dozens of GitHub repos with one command | "Update all my repos in parallel" |

### Workflow Methodologies

Skills that encode proven workflows and prompts for multi-agent development:

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[planning-workflow](skills/planning-workflow/SKILL.md)** | 85%+ time on planning methodology with exact prompts | "How should I plan this feature?" |
| **[beads-workflow](skills/beads-workflow/SKILL.md)** | Converting detailed plans into beads task structure | "Turn this plan into trackable tasks" |
| **[agent-swarm-workflow](skills/agent-swarm-workflow/SKILL.md)** | Multi-agent implementation workflow with marching orders | "How do I coordinate 5 agents on this?" |
| **[agent-fungibility](skills/agent-fungibility/SKILL.md)** | Philosophy of interchangeable generalist agents | "Should I specialize my agents?" |
| **[ui-ux-polish](skills/ui-ux-polish/SKILL.md)** | Iterative Stripe-level UI polish with exact prompt | "Make this look world-class" |
| **[de-slopify](skills/de-slopify/SKILL.md)** | Remove AI writing artifacts from documentation | "Clean up the AI slop in this README" |
| **[tanstack-integration](skills/tanstack-integration/SKILL.md)** | Strategic TanStack library adoption (avoid man-with-hammer) | "Should I use TanStack Query here?" |

### Discord Integration

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[flywheel-discord](skills/flywheel-discord/SKILL.md)** | Security rules for Discord community assistant | "Respond to Discord without leaking secrets" |

### Cloud & Infrastructure

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[gcloud](skills/gcloud/SKILL.md)** | Google Cloud Platform - Compute, Cloud Run, GKE, Storage, BigQuery, etc. | "Deploy to Cloud Run in us-central1" |
| **[wrangler](skills/wrangler/SKILL.md)** | Cloudflare Workers, KV, R2, D1, Pages | "Deploy the worker and tail logs" |
| **[vercel](skills/vercel/SKILL.md)** | Vercel deployments, domains, env vars | "Deploy to production" |
| **[supabase](skills/supabase/SKILL.md)** | Supabase DB, migrations, Edge Functions, storage | "Run migrations and generate types" |

### Browser Automation

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[claude-chrome](skills/claude-chrome/SKILL.md)** | Claude in Chrome - control your authenticated browser, automate workflows, fill forms, extract data | "Open Gmail and draft replies to unread emails" |

### Media & Image Tools

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[giil](skills/giil/SKILL.md)** | Get Image [from] Internet Link - download full-resolution images from iCloud, Dropbox, Google Photos, Google Drive share links | "Download this screenshot: https://share.icloud.com/..." |

### Documentation & Export

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[csctf](skills/csctf/SKILL.md)** | Chat Shared Conversation To File - convert ChatGPT, Gemini, Grok, and Claude share links to clean Markdown + HTML transcripts | "Save this conversation: https://chatgpt.com/share/..." |

### Communication & Telephony

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[clawdtalk](skills/clawdtalk/SKILL.md)** | Phone calling and SMS for OpenClaw. Call your AI agent from any phone with deep tool integration for calendar, Jira, web search, and more. Powered by Telnyx. | "Call my AI agent from mobile to check my schedule" |

### Development Tools

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[github](skills/github/SKILL.md)** | GitHub CLI - repos, issues, PRs, Actions, releases | "Create a PR from this branch" |
| **[ssh](skills/ssh/SKILL.md)** | SSH patterns, tunnels, keys, rsync | "SSH to prod and check logs" |
| **[cursor](skills/cursor/SKILL.md)** | Cursor AI editor CLI | "Open src/auth in Cursor" |
| **[ghostty](skills/ghostty/SKILL.md)** | Ghostty terminal emulator control | "Create a new split pane" |
| **[wezterm](skills/wezterm/SKILL.md)** | WezTerm terminal multiplexer | "Send command to pane 3" |

## Installation

### One-Line Install (Recommended)

Install all skills instantly:

```bash
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/main/install.sh?v=$(date +%s)" | bash -s -- --all
```

Or pick skills interactively:

```bash
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations/main/install.sh?v=$(date +%s)" | bash
```

The installer will:
- Auto-detect your Clawdbot skills directory (`~/clawd/skills` or `~/.clawdbot/skills`)
- Show a categorized menu to pick specific skills (or `--all` to install everything)
- Generate the config snippet for your `clawdbot.json`

#### Installer Options

```bash
# Install all skills
curl ... | bash -s -- --all

# Install to custom directory
curl ... | bash -s -- --dest ~/my-skills

# List available skills
curl ... | bash -s -- --list

# Uninstall all Agent Flywheel skills
curl ... | bash -s -- --uninstall

# Show help
curl ... | bash -s -- --help
```

### Git Clone Install

```bash
# Clone to your skills directory
git clone https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations.git ~/clawdbot-skills

# Run the installer
cd ~/clawdbot-skills && ./install.sh --all
```

### Manual Install

1. Copy desired skill folders to your Clawdbot skills directory:
```bash
cp -r skills/gcloud ~/.clawdbot/skills/
cp -r skills/ntm ~/.clawdbot/skills/
# ... etc
```

2. Enable in your `clawdbot.json`:
```json
{
  "skills": {
    "entries": {
      "ntm": { "enabled": true },
      "agent-mail": { "enabled": true },
      "bv": { "enabled": true },
      "cass": { "enabled": true },
      "cm": { "enabled": true },
      "slb": { "enabled": true },
      "dcg": { "enabled": true },
      "ru": { "enabled": true },
      "planning-workflow": { "enabled": true },
      "beads-workflow": { "enabled": true },
      "agent-swarm-workflow": { "enabled": true },
      "agent-fungibility": { "enabled": true },
      "ui-ux-polish": { "enabled": true },
      "de-slopify": { "enabled": true },
      "tanstack-integration": { "enabled": true },
      "flywheel-discord": { "enabled": true },
      "gcloud": { "enabled": true },
      "wrangler": { "enabled": true },
      "vercel": { "enabled": true },
      "supabase": { "enabled": true },
      "github": { "enabled": true },
      "ssh": { "enabled": true },
      "cursor": { "enabled": true },
      "ghostty": { "enabled": true },
      "wezterm": { "enabled": true }
    }
  }
}
```

3. Restart Clawdbot gateway.

## Prerequisites

Each skill requires its corresponding CLI to be installed:

### Dicklesworthstone Stack

Install via [ACFS](https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup):
```bash
# Clone and run the setup
git clone https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup.git
cd agentic_coding_flywheel_setup
./acfs.sh
```

Or install individual tools:
- **ntm**: `cargo install ntm` or build from source
- **bv**: `cargo install bv` or build from source
- **cass**: `cargo install cass` or build from source
- **cm**: `cargo install cm` or build from source
- **slb**: `cargo install slb` or build from source
- **dcg**: `cargo install dcg` or build from source (Claude Code hook)
- **ru**: Bash script (see [repo](https://github.com/Dicklesworthstone/repo_updater))
- **agent-mail**: Python MCP server (see [repo](https://github.com/Dicklesworthstone/mcp_agent_mail))

### Workflow Skills

The workflow methodology skills (planning-workflow, beads-workflow, agent-swarm-workflow, agent-fungibility, ui-ux-polish, de-slopify, tanstack-integration) are **pure knowledge** and don't require any external tools. They encode proven prompts and workflows.

### Cloud CLIs

```bash
# Google Cloud
brew install google-cloud-sdk

# Cloudflare
npm install -g wrangler

# Vercel
npm install -g vercel

# Supabase
brew install supabase/tap/supabase
```

### Dev Tools

```bash
# GitHub CLI
brew install gh

# Cursor (install app, then CLI is at /usr/local/bin/cursor)

# Ghostty (install app, CLI at /Applications/Ghostty.app/Contents/MacOS/ghostty)

# WezTerm (install app, CLI at /Applications/WezTerm.app/Contents/MacOS/wezterm)
```

## Usage Examples

Once skills are installed and enabled, you can interact naturally:

### Via WhatsApp/Telegram/iMessage:
```
"Deploy the frontend to Vercel"
"Check the CI status on my latest PR"
"Start a multi-agent session for the auth refactor"
"Search my coding history for database migration patterns"
"What rules do we have for error handling?"
"SSH to prod and check the logs"
```

### Via CLI:
```bash
clawdbot agent --message "Deploy the latest to Cloud Run"
clawdbot agent --message "Create a PR for this branch"
clawdbot agent --message "Start 2 Claude agents for the API project"
```

## Skill Anatomy

Each skill is a markdown file with YAML frontmatter:

```markdown
---
name: my-tool
description: "Brief description of what the tool does"
---

# My Tool Skill

Explanation of the tool and how to use it.

## Common Commands

\`\`\`bash
my-tool command --flag value
\`\`\`

## Advanced Usage

More examples...
```

### Key Sections

1. **Frontmatter**: Name and description for Clawdbot's skill index
2. **Overview**: What the tool does and when to use it
3. **Commands**: Copy-paste ready examples with explanations
4. **Workflows**: Common multi-step patterns

## Contributing

### Adding a New Skill

1. Create `skills/<name>/SKILL.md`
2. Include frontmatter with `name` and `description`
3. Document common commands with examples
4. Add to the table in this README
5. Submit a PR

### Improving Existing Skills

- Add missing commands or flags
- Improve descriptions and examples
- Add workflow patterns
- Fix errors or outdated syntax

## Related Projects

- **[Clawdbot](https://github.com/steipete/clawdbot)** - The AI assistant that uses these skills
- **[ACIP](https://github.com/Dicklesworthstone/acip)** - Cognitive inoculation for prompt injection defense
- **[ACFS](https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup)** - Bootstrap for AI dev environments
- **[MCP Agent Mail](https://github.com/Dicklesworthstone/mcp_agent_mail)** - Agent coordination server
- **[Named Tmux Manager](https://github.com/Dicklesworthstone/ntm)** - Multi-agent tmux orchestration
- **[CASS](https://github.com/Dicklesworthstone/coding_agent_session_search)** - Agent session search
- **[CASS Memory](https://github.com/Dicklesworthstone/cass_memory_system)** - Procedural memory for agents
- **[Beads Viewer](https://github.com/Dicklesworthstone/beads_viewer)** - Graph-aware task triage
- **[DCG](https://github.com/Dicklesworthstone/destructive_command_guard)** - Block dangerous commands
- **[Repo Updater](https://github.com/Dicklesworthstone/repo_updater)** - Sync multiple repos

## License

MIT License - See [LICENSE](LICENSE) for details.

---

*Built for the [Agentic Coding Flywheel](https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup) workflow.*
