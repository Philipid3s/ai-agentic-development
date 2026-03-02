# Claude Code - Custom Commands (Plugins)

Custom commands extend Claude Code with slash commands (`/command-name`).
Each command is a `.md` file whose content becomes the agent's system prompt when invoked.

## How It Works

| Location | Scope | Example |
|---|---|---|
| `<project>/.claude/commands/` | Project-only | `/deploy`, `/review` |
| `~/.claude/commands/` | Global (all projects) | `/sentinel` |

- **Filename = command name** - `sentinel.md` becomes `/sentinel`
- **File content = prompt** - defines role, personality, instructions, output format
- **Invoked like any slash command** - `/sentinel` in a Claude Code session

## Installed Commands

### /sentinel (global)
- **Location:** `~/.claude/commands/sentinel.md`
- **Role:** Security specialist - audits code for vulnerabilities
- **Features:** OWASP Top 10 checklist, severity-based findings, structured output format
- **Usage:** `/sentinel` to run a security audit on the current codebase

### andrej-karpathy-skills (community)
- **Source:** https://github.com/forrestchang/andrej-karpathy-skills.git
- **Install:** Clone and copy `.md` files into `~/.claude/commands/`
- **Status:** Not yet installed

### superpowers (community)
- **Source:** https://github.com/obra/superpowers.git
- **Install:** Clone and copy `.md` files into `~/.claude/commands/`
- **Status:** Not yet installed

## Creating a New Command

1. Create a `.md` file in `~/.claude/commands/` (global) or `.claude/commands/` (project)
2. Define the agent's role, instructions, and output format
3. Invoke with `/filename` in any Claude Code session

See [sentinel.md](~/.claude/commands/sentinel.md) for a well-structured example.

