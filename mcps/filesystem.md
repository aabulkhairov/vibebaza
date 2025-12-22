---
title: Filesystem MCP
description: MCP server for secure filesystem operations with configurable access
  controls.
tags:
- Filesystem
- Files
- Directory
- Official
author: Anthropic
featured: true
install_command: claude mcp add filesystem -- npx -y @modelcontextprotocol/server-filesystem
  ~/Documents
connection_type: stdio
paid_api: false
---

The Filesystem MCP server provides Claude with secure access to your local filesystem with configurable access controls.

## Installation

```bash
npm install -g @modelcontextprotocol/server-filesystem
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/path/to/allowed/directory"
      ]
    }
  }
}
```

## Available Tools

### read_file
Read the contents of a file.

```typescript
read_file(path: string): string
```

### write_file
Write content to a file.

```typescript
write_file(path: string, content: string): void
```

### list_directory
List contents of a directory.

```typescript
list_directory(path: string): FileInfo[]
```

### create_directory
Create a new directory.

```typescript
create_directory(path: string): void
```

### move_file
Move or rename a file.

```typescript
move_file(source: string, destination: string): void
```

### search_files
Search for files matching a pattern.

```typescript
search_files(path: string, pattern: string): string[]
```

## Security

- Access is restricted to specified directories
- No access to parent directories (`..`)
- Configurable read/write permissions
- Path validation and sanitization

## Usage Example

```
Claude, please read the contents of ./config/settings.json
and update the database connection string.
```
