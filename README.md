# Claude, Document This!

[![Claude Code](https://img.shields.io/badge/Claude-Code-8A2BE2)](https://github.com/anthropics/claude-code)
[![Claude Code Projects Index](https://img.shields.io/badge/My_Claude_Code-Projects-blue)](https://github.com/danielrosehill/Claude-Code-Repos-Index)
[![GitHub Master Index](https://img.shields.io/badge/GitHub-Master_Index-green)](https://github.com/danielrosehill/Github-Master-Index)

---

## The Need

Claude Code is extremely useful for systems administration.

OS admin can be done on local environments or on the server. 

Guardrails aside, it's prudent to note, carefully, what changes were undertaken. 

Claude is good at delivering these logs unsolicited via the terminal. 

But without some external tooling, those logs will remain there - printed to the terminal. Obviously this is not a viable format for long term retention.

---

## Ways To Skin This Cat

As is now commonplace in AI, the challenge is less *"how could this possibly be done?"* and more *"from the various ways in which I could do this, which makes the most sense?"*

I am sharing this repo to offer a couple of methods I've had success with.

---

### 1: MCP to Anything (Notion, Confluence, Google Drive, Email & More!)

This is a great use for user level MCPs (the type that are always and can thus be accessed from wherever Claude happens to be on your OS).

Many platforms have reliable MCPs or can be accessed through existing tools:

- **Notion** - Reliable MCP for creating documentation pages
- **Confluence** - Document system changes in your team wiki
- **Google Drive** - Save to Docs for easy sharing and collaboration
- **Email** - Simple but effective - email fixes to yourself for later reference
- **Slack/Discord** - Post to channels for team visibility

The slash command here can be (approximately):

**For Notion:**

*"Thanks for fixing that. Please now invoke Notion MCP to create a new page documenting, in detail, the fix that we just applied. Ensure that you capture this in an orderly fashion noting the problem, the remediation, and today's date."*

**For Email:**

*"Thanks for fixing that. Please email me a detailed summary of the fix we just applied, including the problem, solution, and any relevant commands or file changes."*

**Pro Tip:** If you have a catch-all email setup, create a dedicated address like `claude-logs@yourdomain.com` to automatically organize all AI-generated fix documentation in a single email folder/tag, keeping your main inbox clean.

**For Google Drive:**

*"Please create a Google Doc summarizing this fix and save it to my 'System Administration' folder in Drive."*

Sometimes, it's hard to know whether a case like this is best tackled through a subagent or slash command or both. 

The answer may be the extent to which you want the operation to be autonomous. If you *do* then subagents might be warranted. The autonomous thinking here might be: *"would the user prefer this to be emailed to them, shared in Google Drive, or added to their personal notebook? I'll figure that out and then run the relevant slash command"*

In that model you might have:

- Subagent for creating these logbook entries 
- Slash commands instructing how to use specific MCPs with target-specific formatting instructions 

In the simple implementation we just have a slash command: write out a note and put it here, basically.

---

### 2: Obsidian Notebooks 

I love Obsidian notebooks!

They work a treat with Claude Code because they are perfect for storing wikis/information.

When I ask Claude to document something it did on my system, my motivations are usually multiple:

1) Tell me what you did just in case it turns out to be a horribly misguided decision that went above my head and I need to clean this up later (minority of cases)
2) Tell me what you did so I can keep good documentation (all cases) 
3) Tell me what you did so that I can learn more about this for my own education (most cases) 

To make this work you can just:

- Create an Obsidian notebook for storing "stuff AI figures out"  
- Write a slash command asking Claude to write an entry there and then push the repo 


This way:

- The information gets predictably documented in a notebook that you can even keep just for AI agent authored content (or mix it up!) 
- Claude even takes care of pushing it to Github 

I have an Obsidian notebook called "Notes From AI"

`/home/daniel/obsidian-notebooks/notes-from-ai`

I add this instruction to my home folder `CLAUDE.md` (or approximately):

*"Sometimes I might ask you to document things for my own reference. If so document them here."*

What's nice, too, is that you can even ask Claude to keep the mess in order.

Something like:

*"Document this in the 'Notes from AI' Obsidian notebook at {path}. Save it into a logical subfolder. For example: GPU-Fixes. If it doesn't exist, create it. If the note should be in a subfolder, create it."* (etc).

---

## Example Configurations

This repository includes example slash commands and agents to demonstrate different approaches to documenting system fixes:

| File | Type | Purpose | Link |
|------|------|---------|------|
| `save-to-notion.md` | Slash Command | Creates a detailed logbook entry in Notion using Notion MCP | [View](example-slashes/save-to-notion.md) |
| `save-to-obsidian.md` | Slash Command | Documents changes in an Obsidian notebook with Git push | [View](example-slashes/save-to-obsidian.md) |
| `email-me-the-fix.md` | Slash Command | Sends summary email via Resend MCP with platform references | [View](example-slashes/email-me-the-fix.md) |
| `fix-documenter.md` | Agent | Orchestrates documentation across multiple platforms based on user preference | [View](example-agents/fix-documenter.md) |

### Using the Agent vs Slash Commands

**Slash Commands** are best when you:
- Know exactly which platform you want to use
- Want direct, immediate documentation
- Prefer manual control over the process

**Fix Documenter Agent** is best when you:
- Want to be asked where to document the fix
- Need documentation across multiple platforms
- Prefer an intelligent assistant that handles the workflow
- Want cross-references between platforms automatically

---

To view an index of my Claude Code related projects, [click here](https://github.com/danielrosehill/Claude-Code-Repos-Index).
