---
title: Box MCP
description: Securely connect AI agents to your enterprise content in Box with AI-powered
  file queries, collaboration, and document management.
tags:
- File Management
- Enterprise
- Collaboration
- Storage
- Documents
author: Box
featured: true
install_command: claude mcp add box -- uvx mcp-server-box
connection_type: stdio
paid_api: false
---

The Box MCP Server enables AI agents to securely access and interact with enterprise content stored in Box, providing AI-powered file operations, search, and collaboration features.

## Installation

### Using uvx

```bash
uvx mcp-server-box
```

### Using pip

```bash
pip install mcp-server-box
```

## Configuration

### OAuth2.0 Authentication

```json
{
  "mcpServers": {
    "box": {
      "command": "uvx",
      "args": ["mcp-server-box"],
      "env": {
        "BOX_CLIENT_ID": "your_client_id",
        "BOX_CLIENT_SECRET": "your_client_secret",
        "BOX_REDIRECT_URL": "http://localhost:8000/callback"
      }
    }
  }
}
```

## Available Tools

### AI Operations
| Tool | Description |
|------|-------------|
| `box_tools_ai` | AI-powered file and hub queries |

### File Operations
| Tool | Description |
|------|-------------|
| `box_tools_files` | File operations (read, upload, download) |
| `box_tools_folders` | Folder operations (list, create, delete, update) |
| `box_tools_search` | Search files and folders |

### Collaboration
| Tool | Description |
|------|-------------|
| `box_tools_collaboration` | Manage file/folder collaborations |
| `box_tools_shared_links` | Shared link management |
| `box_tools_tasks` | Task and task assignment management |
| `box_tools_comments` | Comment operations |

### Administration
| Tool | Description |
|------|-------------|
| `box_tools_users` | User management and queries |
| `box_tools_groups` | Group management |
| `box_tools_metadata` | Metadata template and instance management |

## Transport Options

### STDIO Mode (Default)

```bash
uvx mcp-server-box
```

### HTTP Mode

```bash
uvx mcp-server-box --transport http --port 8005
```

## Features

- **Enterprise Security** - Secure OAuth 2.0 authentication
- **AI-Powered Queries** - Natural language file and content queries
- **Full API Coverage** - Comprehensive Box API access
- **Multiple Auth Types** - OAuth, CCG, JWT, and MCP client auth

## Usage Examples

```
Search for all PDF files in the Marketing folder
```

```
Create a shared link for the Q4 Report document
```

```
List all collaborators on the Project Alpha folder
```

## Resources

- [GitHub Repository](https://github.com/box-community/mcp-server-box)
- [Box Developer Documentation](https://developer.box.com/)
- [Authentication Guide](https://github.com/box-community/mcp-server-box/blob/main/docs/authentication.md)
