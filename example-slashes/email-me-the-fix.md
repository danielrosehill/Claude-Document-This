# Email Me The Fix

Use the Resend MCP to send a detailed email documenting the system fix that was just applied.

## Instructions

Send an email to daniel@danielrosehill.co.il using the Resend MCP with the following configuration:

**Sender:** claude@danielrosehill.co.il
**Sender Name:** Claude Code
**Subject:** System Fix Applied: [Brief Description]

## Email Content

The email should include:

1. **Date and Time:** Include today's date and approximate time of the fix
2. **Problem Description:** What issue was identified and needed fixing
3. **Solution Applied:** Detailed explanation of the fix that was implemented
4. **Commands/Changes:** List any commands run or files modified
5. **Verification:** Note any verification steps taken to confirm the fix works
6. **References:** If this email follows Notion or Obsidian documentation:
   - Include link to Notion page (if created)
   - Reference Obsidian notebook location (if saved)
7. **Follow-up:** Any recommended monitoring or follow-up actions

## Format

Use clean HTML formatting with proper structure:
- Clear headings for each section
- Code blocks for commands
- Bullet points for lists
- Professional but concise tone

## Example Workflow

This slash command works well in sequence:

1. Apply the fix
2. `/save-to-notion` - Document in Notion
3. `/save-to-obsidian` - Save to Obsidian notebook
4. `/email-me-the-fix` - Send summary email with references to both

This creates a comprehensive documentation trail across multiple platforms for important system changes.
