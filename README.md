# AI Agent Developer Environment Setup

## Your Name
Alkaeya De la Pena

## Workshop Cohort
Winter 2026 Cohort

## Development Environment Checklist

### ✅ Node.js Installed
![Node.js Version](screenshots/node-version.png)
Command: `node --version`

### ✅ Git Installed
![Git Version](screenshots/git-version.png)
Command: `git --version`

### ✅ VS Code Insider Running with GitHub Copilot Enabled
![VS Code](screenshots/vscode-insider.png)

### ✅ Claude Desktop Open with Working MCP Servers Connected
![Claude Desktop](screenshots/claude-desktop.png)

## MCP Servers Purpose and Functionality

### ✅ GitHub MCP Server
**Status:** Working

**Purpose:** Provides direct access to GitHub API for repository management and interaction.

**Functionality:**
- List repositories and view repository details
- Access repository metadata and statistics
- Integrate with GitHub workflows directly from Claude Desktop
- Query commit history and pull request information

**Test Command:** "List my GitHub repositories using the GitHub MCP server"

### ✅ Memory MCP Server
**Status:** Working

**Purpose:** Enables AI agents to maintain persistent memory across conversations and sessions.

**Functionality:**
- Store and retrieve information between conversations
- Maintain context about user preferences and past interactions
- Support multi-turn conversations with state persistence
- Enable agents to remember important facts and decisions

**Test Command:** "Remember that my name is Alkaeya De la Pena, and I'm in the Winter 2026 Cohort"

## Why These 2 Servers?

Initially, the bootcamp required 4 MCP servers (Rolldice, Calendar Booking, Bootcamp AI Agent, and GitHub). However, during implementation, I encountered the following:

- **Rolldice:** No official MCP server exists in the npm registry. Community alternatives tested didn't provide functional implementations.
- **Calendar Booking:** Requires Cal.com-specific credentials and custom setup not available in public repositories.
- **Bootcamp AI Agent:** Appears to be a custom server requiring configuration from bootcamp administrators.

The 2 servers documented here (GitHub and Memory) represent the officially supported, publicly available MCP servers that have been verified as working.

## Troubleshooting Notes

### GitHub Token Configuration
**Issue:** Initial attempts to use GitHub MCP server failed due to missing authentication.

**Solution:** Generated a GitHub Personal Access Token with appropriate permissions and configured it in the MCP server environment variables:
```bash
"env": {
  "GITHUB_PERSONAL_ACCESS_TOKEN": "your-token-here"
}
```

### Filesystem Server Issues
**Issue:** Earlier attempts to add a filesystem MCP server resulted in "Server disconnected" errors during initialization.

**Solution:** Removed the filesystem server from the active configuration to maintain system stability. The core functionality was available through GitHub MCP server instead.

### JSON Parsing Errors with Non-existent Servers
**Issue:** Attempted to add Rolldice and other community MCP servers resulted in JSON parsing errors and "transport not found" messages.

**Solution:** Verified that only officially published npm packages work reliably. Limited configuration to packages in the @modelcontextprotocol namespace available on npm registry.

### MCP Server Discovery Strategy
**Lesson Learned:** Not all MCP servers mentioned in documentation exist in the npm registry. Always verify package existence with:
```bash
npm view @modelcontextprotocol/server-name
```
Before adding to configuration.