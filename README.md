# Claude Fix Logger

[![Claude Code Plugin](https://img.shields.io/badge/Claude_Code-Plugin-8A2BE2)](https://github.com/anthropics/claude-code)
[![Version](https://img.shields.io/badge/version-1.0.0-blue)](https://github.com/danielrosehill/Claude-Fix-Logger)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

A Claude Code plugin for documenting system administration fixes and changes across multiple platforms (Notion, Obsidian, Email).

---

## Overview

System administration with Claude Code is powerful, but those terminal outputs documenting what changed aren't suitable for long-term retention. **Claude Fix Logger** solves this by providing commands and agents to automatically capture comprehensive fix documentation across your preferred platforms.

## Features

- **Multiple Documentation Platforms**: Save to Notion, Obsidian, or email
- **Intelligent Agent**: Orchestrates documentation across platforms based on your preference
- **Structured Templates**: Consistent formatting for problem/solution documentation
- **Cross-Platform References**: Links between Notion, Obsidian, and email for comprehensive trails
- **MCP Integration**: Leverages Notion, Resend, and Time MCPs for seamless automation

---

## Installation

Available via [Daniel's Claude Code Plugins Marketplace](https://github.com/danielrosehill/Claude-Code-Plugins).

---

## Commands

### `/save-to-notion`

Creates a detailed logbook entry in Notion using the Notion MCP.

**Usage:**
```
/save-to-notion
```

**Requirements:**
- Notion MCP configured
- Time MCP (optional, for accurate timestamps)

**What it does:**
- Gets current date/time
- Formats fix documentation with problem/solution structure
- Creates page in your Notion workspace
- Confirms successful creation

---

### `/save-to-obsidian`

Documents changes in an Obsidian notebook and pushes to GitHub.

**Usage:**
```
/save-to-obsidian
```

**Configuration:**
Update the path in [commands/save-to-obsidian.md](commands/save-to-obsidian.md) to match your Obsidian notebook location (default: `/home/daniel/obsidian-notebooks/notes-from-ai`).

**What it does:**
- Creates markdown note in your Obsidian vault
- Organizes into logical subfolders (e.g., "GPU-Fixes")
- Pushes notebook to GitHub
- Provides file path confirmation

---

### `/email-me-the-fix`

Sends comprehensive email summary via Resend MCP.

**Usage:**
```
/email-me-the-fix
```

**Requirements:**
- Resend MCP configured

**Configuration:**
Update recipient and sender addresses in [commands/email-me-the-fix.md](commands/email-me-the-fix.md).

**What it does:**
- Formats fix documentation in clean HTML
- Includes references to Notion/Obsidian docs if created
- Sends to dedicated email (e.g., `claude-logs@yourdomain.com`)
- Provides confirmation of send

**Pro Tip:** Use a dedicated email address like `claude-logs@yourdomain.com` to organize all AI-generated fix documentation in a single email folder/tag.

---

## Agent

### `fix-documenter`

An intelligent agent that orchestrates documentation across multiple platforms based on your preference.

**How to invoke:**
Claude Code will automatically suggest this agent when you complete a system fix, or you can explicitly invoke it:
```
Please document this fix
```

**What it does:**
1. Analyzes the conversation to understand the fix applied
2. Asks which platform(s) you prefer (Notion, Obsidian, Email, or all)
3. Executes the appropriate slash commands in sequence
4. Includes cross-references when using multiple platforms
5. Confirms completion with summary of what was documented

**Example interaction:**
```
User: "Great, that fixed the GPU driver issue!"

Agent: "Excellent! Where would you like me to document this GPU driver fix?

Options:
1. Notion - Structured page in your Notion workspace
2. Obsidian - Markdown note in your 'Notes From AI' notebook
3. Email - Summary sent to your email
4. All three - Complete documentation trail

What's your preference?"

User: "All three please"

Agent: [Executes /save-to-notion, /save-to-obsidian, /email-me-the-fix]
```

---

## Configuration

### MCP Requirements

This plugin works best with the following MCPs configured:

| MCP | Required For | Optional? |
|-----|--------------|-----------|
| **Notion** | `/save-to-notion` command | Yes |
| **Resend** | `/email-me-the-fix` command | Yes |
| **Time** | Accurate timestamps | Yes |

All MCPs are optional - commands that require unavailable MCPs simply won't function.

### Customizing Paths

**Obsidian Notebook:**
Edit [commands/save-to-obsidian.md](commands/save-to-obsidian.md) line 7:
```markdown
/home/your-username/obsidian-notebooks/your-notebook-name
```

**Email Recipients:**
Edit [commands/email-me-the-fix.md](commands/email-me-the-fix.md) lines 7-12 to update sender/recipient addresses.

---

## Documentation Template

All commands follow this consistent structure:

```markdown
# Fix Title

## Problem
Summarize the problem that was resolved or what was optimized.

## Fix
Summarize the fix/remediation/optimization.

If several failed approaches were tried first, note them only if
that information might be significant in the future. Otherwise,
just document what worked.
```

**Formatting Guidelines:**
- Code blocks in fenced code blocks
- Clear headings and subheadings
- Professional but concise tone
- Includes metadata (date, time, verification)

---

## Use Cases

### 1. Quick Single-Platform Documentation
```bash
# Just fixed something, save to Obsidian
/save-to-obsidian
```

### 2. Comprehensive Multi-Platform Trail
```bash
# Important fix, document everywhere
/save-to-notion
/save-to-obsidian
/email-me-the-fix
```

### 3. Intelligent Agent Orchestration
```bash
User: "Fixed the kernel panic issue!"
User: "Please document this"
# Agent asks preference and handles the workflow
```

---

## Plugin Structure

```
claude-fix-logger/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── commands/
│   ├── save-to-notion.md    # Notion documentation command
│   ├── save-to-obsidian.md  # Obsidian documentation command
│   └── email-me-the-fix.md  # Email summary command
├── agents/
│   └── fix-documenter.md    # Orchestration agent
├── LICENSE
├── CHANGELOG.md
└── README.md
```

---

## Why Document System Fixes?

When using Claude Code for system administration, documenting changes is crucial for:

1. **Accountability**: Know exactly what was changed and when
2. **Learning**: Build a personal knowledge base of solutions
3. **Recovery**: Quickly understand and reverse changes if needed
4. **Team Sharing**: Communicate fixes to team members
5. **Compliance**: Maintain audit trails for regulated environments

Without external tooling, terminal outputs are ephemeral. This plugin ensures your hard-won solutions are captured and organized.

---

## Examples

### GPU Driver Fix Documentation
After resolving a GPU driver issue, run `/save-to-obsidian` to create:

```markdown
# AMD ROCm Driver Fix - 2025-11-16

## Problem
ROCm was failing to detect GPU after kernel update to 6.14.0-15

## Fix
Reinstalled ROCm with proper kernel headers:
```bash
sudo apt install linux-headers-$(uname -r)
sudo apt reinstall rocm-dkms
sudo reboot
```

Verification: `rocm-smi` now shows GPU properly
```

### Networking Issue Trail
For a complex networking fix, use the agent to document across all platforms:
- Notion: Detailed technical reference with diagrams
- Obsidian: Quick reference in "Network-Fixes" folder
- Email: Summary with links to both for easy access

---

## Contributing

Contributions welcome! Please feel free to submit issues or pull requests.

### Development

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test with Claude Code
5. Submit a pull request

---

## License

MIT License - see [LICENSE](LICENSE) for details.

---

## Author

**Daniel Rosehill**
- Website: [danielrosehill.com](https://danielrosehill.com)
- Email: public@danielrosehill.com
- GitHub: [@danielrosehill](https://github.com/danielrosehill)

---

## Related Projects

- [Claude Code Repos Index](https://github.com/danielrosehill/Claude-Code-Repos-Index) - My other Claude Code projects
- [GitHub Master Index](https://github.com/danielrosehill/Github-Master-Index) - All my GitHub repositories

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history and updates.
