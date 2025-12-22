---
title: Canva Dev MCP
description: AI-powered development assistance for building Canva apps and integrations
  with access to App UI Kit documentation and SDK reference.
tags:
- Design
- Development
- Documentation
- SDK
- Creative
author: Canva
featured: false
install_command: claude mcp add canva-dev -- npx -y @canva/cli@latest mcp
connection_type: stdio
paid_api: false
---

The Canva Dev MCP Server provides AI-powered development assistance for building Canva apps and integrations, with direct access to App UI Kit documentation and SDK references.

## Installation

```bash
claude mcp add canva-dev -- npx -y @canva/cli@latest mcp
```

## Configuration

### Claude Code

```bash
claude mcp add canva-dev -- npx -y @canva/cli@latest mcp
```

### Claude Desktop

```json
{
  "mcpServers": {
    "canva-dev": {
      "command": "npx",
      "args": ["-y", "@canva/cli@latest", "mcp"]
    }
  }
}
```

### Cursor

Create `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "canva-dev": {
      "command": "npx",
      "args": ["-y", "@canva/cli@latest", "mcp"]
    }
  }
}
```

### VS Code

Create `.vscode/mcp.json`:

```json
{
  "servers": {
    "canva-dev": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@canva/cli@latest", "mcp"]
    }
  }
}
```

## Features

- **App UI Kit Documentation** - Access to all UI component documentation
- **Apps SDK Reference** - Complete SDK API reference
- **Development Assistance** - AI-powered help for Canva app development
- **Local Processing** - Server runs locally, fetches docs from canva.dev

## Usage Notes

MCP tools are LLM-controlled and invoked through relevant keywords:
- "App UI Kit" - For UI component documentation
- "Apps SDK" - For SDK API reference
- Canva documentation references

## Usage Examples

```
How many components are in the App UI Kit?
```

```
How do I create a button in a Canva app?
```

```
What scopes are available for Canva apps?
```

## Security and Privacy

- Server operates locally on your device
- Fetches Canva documentation from canva.dev
- Does not transmit your code or prompts to external sources

## Resources

- [Canva Dev MCP Documentation](https://www.canva.dev/docs/apps/mcp-server/)
- [Canva Apps SDK](https://www.canva.dev/docs/apps/)
- [App UI Kit](https://www.canva.dev/docs/apps/app-ui-kit/)
