# Agent Flywheel Clawdbot Skills & Integrations

> A curated collection of [Clawdbot](https://github.com/anthropics/clawdbot) skills for professional agentic coding workflows. Includes skills for the [Agentic Coding Flywheel Setup (ACFS)](https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup) toolkit and popular cloud/dev infrastructure CLIs.

## What Are Clawdbot Skills?

Skills are markdown files that teach Clawdbot (Anthropic's multi-surface AI assistant) how to use command-line tools. Each skill contains:
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
| **[bv](skills/bv/SKILL.md)** | Beads Viewer - TUI for task management with dependency graphs | "Show me the task graph for current sprint" |
| **[cass](skills/cass/SKILL.md)** | Coding Agent Session Search - unified history from all AI coding agents | "Search my history for auth implementations" |
| **[cm](skills/cm/SKILL.md)** | CASS Memory System - procedural memory and rule playbook | "What patterns did we learn from the refactor?" |
| **[slb](skills/slb/SKILL.md)** | Simultaneous Launch Button - two-person rule for dangerous commands | "Run the migration with peer review" |

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

### Development Tools

| Skill | Description | Use Case |
|-------|-------------|----------|
| **[github](skills/github/SKILL.md)** | GitHub CLI - repos, issues, PRs, Actions, releases | "Create a PR from this branch" |
| **[ssh](skills/ssh/SKILL.md)** | SSH patterns, tunnels, keys, rsync | "SSH to prod and check logs" |
| **[cursor](skills/cursor/SKILL.md)** | Cursor AI editor CLI | "Open src/auth in Cursor" |
| **[ghostty](skills/ghostty/SKILL.md)** | Ghostty terminal emulator control | "Create a new split pane" |
| **[wezterm](skills/wezterm/SKILL.md)** | WezTerm terminal multiplexer | "Send command to pane 3" |

## Installation

### Quick Install

```bash
# Clone to your skills directory
git clone https://github.com/Dicklesworthstone/agent_flywheel_clawdbot_skills_and_integrations.git ~/clawdbot-skills

# Symlink to clawdbot workspace
mkdir -p ~/.clawdbot/skills
for skill in ~/clawdbot-skills/skills/*/; do
  ln -sf "$skill" ~/.clawdbot/skills/
done
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
      "gcloud": { "enabled": true },
      "ntm": { "enabled": true },
      "agent-mail": { "enabled": true },
      "bv": { "enabled": true },
      "cass": { "enabled": true },
      "cm": { "enabled": true },
      "slb": { "enabled": true },
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
- **agent-mail**: Python MCP server (see [repo](https://github.com/Dicklesworthstone/mcp_agent_mail))

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

- **[Clawdbot](https://github.com/anthropics/clawdbot)** - The AI assistant that uses these skills
- **[ACFS](https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup)** - Bootstrap for AI dev environments
- **[MCP Agent Mail](https://github.com/Dicklesworthstone/mcp_agent_mail)** - Agent coordination server
- **[Named Tmux Manager](https://github.com/Dicklesworthstone/ntm)** - Multi-agent tmux orchestration
- **[CASS](https://github.com/Dicklesworthstone/cass)** - Agent session search
- **[Beads Viewer](https://github.com/Dicklesworthstone/bv)** - Task management TUI

## License

MIT License - See [LICENSE](LICENSE) for details.

---

*Built for the [Agentic Coding Flywheel](https://github.com/Dicklesworthstone/agentic_coding_flywheel_setup) workflow.*
