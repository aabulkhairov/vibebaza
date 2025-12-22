---
title: Notion MCP
description: Official Notion integration for AI assistants to search, create, and
  manage pages, databases, and content in Notion workspaces.
tags:
- Productivity
- Documentation
- Knowledge Base
- Workspace
- Notes
author: Notion
featured: true
install_command: claude mcp add notion -e NOTION_TOKEN=ntn_your_token -- npx -y @notionhq/notion-mcp-server
connection_type: http
paid_api: true
---

The official Notion MCP server enables AI assistants to interact with Notion workspaces, allowing searching, creating, and managing pages, databases, and content through natural language.

## Installation

```bash
npm install -g @notionhq/notion-mcp-server
# or use npx directly
npx -y @notionhq/notion-mcp-server
```

## Configuration

### Using NOTION_TOKEN (Recommended)

```json
{
  "mcpServers": {
    "notionApi": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "NOTION_TOKEN": "ntn_****"
      }
    }
  }
}
```

### Using Docker

```json
{
  "mcpServers": {
    "notionApi": {
      "command": "docker",
      "args": [
        "run", "--rm", "-i",
        "-e", "NOTION_TOKEN",
        "mcp/notion"
      ],
      "env": {
        "NOTION_TOKEN": "ntn_****"
      }
    }
  }
}
```

### Remote MCP Server (OAuth)

Notion also offers a remote MCP server with OAuth authentication. Learn more at [Notion MCP Docs](https://developers.notion.com/docs/mcp).

## Setup Steps

### 1. Create Integration

1. Go to [Notion Integrations](https://www.notion.so/profile/integrations)
2. Create a new **internal** integration
3. Copy the integration token

### 2. Connect Pages

Grant your integration access to pages:
- Go to **Access** tab in integration settings
- Select pages to connect
- Or use page menu → "Connect to integration"

## Available Tools

### Page Operations
- `notion_search` - Search pages and databases
- `notion_get_page` - Retrieve page content
- `notion_create_page` - Create new pages
- `notion_update_page` - Update existing pages

### Database Operations
- Query databases
- Create database entries
- Update database properties

### Block Operations
- Read block content
- Append blocks to pages
- Update block content

### Comment Operations
- Add comments to pages
- Retrieve page comments

## Transport Options

### STDIO Transport (Default)

```bash
npx @notionhq/notion-mcp-server
```

### Streamable HTTP Transport

```bash
npx @notionhq/notion-mcp-server --transport http --port 3000
```

With authentication:

```bash
npx @notionhq/notion-mcp-server --transport http --auth-token "your-secret-token"
```

## Features

- **Full API Coverage** - Access to Notion's complete API
- **Read-Only Option** - Configure integration for read-only access
- **OAuth Support** - Remote server supports OAuth authentication
- **Docker Support** - Official Docker image available

## Usage Examples

```
Comment "Hello MCP" on page "Getting started"
```

```
Add a page titled "Notion MCP" to page "Development"
```

```
Get the content of page 1a6b35e6e67f802fa7e1d27686f017f2
```

## Security

Configure integration capabilities for security:
- Read-only: Enable only "Read content" in Configuration tab
- Limited access: Connect only required pages

## Resources

- [Notion MCP Documentation](https://developers.notion.com/docs/mcp)
- [GitHub Repository](https://github.com/makenotion/notion-mcp-server)
- [Notion API Reference](https://developers.notion.com/reference/intro)
