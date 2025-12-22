---
title: E2B MCP
description: Official E2B MCP server for secure code execution in cloud sandboxes,
  enabling AI assistants to run code safely.
tags:
- Code Execution
- Sandbox
- AI
- Development
- Security
author: E2B
featured: true
install_command: claude mcp add e2b -e E2B_API_KEY=your_key -- npx -y @e2b/mcp-server
connection_type: stdio
paid_api: true
---

The E2B MCP Server allows AI assistants to execute code safely in secure cloud sandboxes. It provides code interpreting capabilities through the E2B Sandbox infrastructure.

## Installation

### Via Smithery

```bash
npx @smithery/cli install e2b --client claude
```

### Manual Installation

```bash
npm install -g @e2b/mcp-server
```

### Claude Code

```bash
claude mcp add e2b -e E2B_API_KEY=YOUR_API_KEY -- npx -y @e2b/mcp-server
```

## Configuration

### Claude Desktop

```json
{
  "mcpServers": {
    "e2b": {
      "command": "npx",
      "args": ["-y", "@e2b/mcp-server"],
      "env": {
        "E2B_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Features

- **Secure Code Execution** - Run AI-generated code in isolated cloud sandboxes
- **Multiple Languages** - Support for Python, JavaScript, and more
- **File System Access** - Read and write files within the sandbox
- **Package Installation** - Install dependencies on the fly
- **Persistent Sessions** - Maintain state across multiple code executions

## Editions

The E2B MCP server is available in two editions:

- **JavaScript** - For Node.js environments
- **Python** - For Python environments

## Usage Examples

```
Run this Python code and show me the output
```

```
Create a data visualization using matplotlib
```

```
Execute this JavaScript and return the result
```

## Security

E2B sandboxes provide:
- Isolated execution environments
- No access to host system
- Automatic cleanup after execution
- Resource limits and timeouts

## Resources

- [GitHub Repository](https://github.com/e2b-dev/mcp-server)
- [E2B Documentation](https://e2b.dev/docs)
- [E2B Platform](https://e2b.dev/)
- [Smithery](https://smithery.ai/server/e2b)
