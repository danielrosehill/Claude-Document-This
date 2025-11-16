# Changelog

All notable changes to the Claude Fix Logger plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-11-16

### Added
- Initial release of Claude Fix Logger plugin
- `/save-to-notion` command for documenting fixes in Notion
- `/save-to-obsidian` command for documenting fixes in Obsidian notebooks
- `/email-me-the-fix` command for sending fix summaries via email
- `fix-documenter` agent for intelligent orchestration across platforms
- Comprehensive documentation and examples
- MCP integration for Notion, Resend, and Time services
- Structured documentation templates for consistency
- Cross-platform reference support

### Changed
- Refactored from example repository to proper Claude Code plugin structure
- Reorganized directory structure to follow plugin conventions
- Updated README with comprehensive installation and usage instructions

### Plugin Structure
- `.claude-plugin/plugin.json` - Plugin manifest
- `commands/` - Slash command definitions
- `agents/` - Agent definitions
- Complete documentation and licensing

---

## Future Enhancements

Planned features for future releases:

- Additional platform integrations (Confluence, Google Drive, etc.)
- Custom template support
- Automated categorization of fix types
- Search and retrieval capabilities
- Fix history analytics
- Team collaboration features

---

For more information, visit: https://github.com/danielrosehill/Claude-Fix-Logger
