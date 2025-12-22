---
title: Google Drive MCP
description: Google Drive integration for searching, reading, and managing files in
  your Google Drive.
tags:
- Google Drive
- Cloud Storage
- Files
- Documents
author: Anthropic
featured: true
install_command: claude mcp add gdrive -- npx -y @modelcontextprotocol/server-gdrive
connection_type: stdio
paid_api: false
---

The Google Drive MCP server provides integration with Google Drive, allowing Claude to search for files, read document contents, and access your cloud storage.

## Installation

```bash
npm install -g @modelcontextprotocol/server-gdrive
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "gdrive": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-gdrive"]
    }
  }
}
```

## Authentication Setup

1. Create a project in [Google Cloud Console](https://console.cloud.google.com/)
2. Enable the Google Drive API
3. Create OAuth 2.0 credentials (Desktop application type)
4. Download the credentials file
5. Set the path to credentials:

```json
{
  "mcpServers": {
    "gdrive": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-gdrive"],
      "env": {
        "GOOGLE_APPLICATION_CREDENTIALS": "/path/to/credentials.json"
      }
    }
  }
}
```

## Available Tools

### search_files
Search for files in Google Drive.

```typescript
search_files(query: string): FileList
```

**Parameters:**
- `query` - Search query (supports Drive search syntax)

### read_file
Read the contents of a file.

```typescript
read_file(file_id: string): FileContent
```

### list_files
List files in a folder.

```typescript
list_files(folder_id?: string): FileList
```

## Resources

The server also exposes files as MCP resources:
- `gdrive:///<file_id>` - Access any file by ID
- Supports Google Docs, Sheets, and other formats

## Supported File Types

- Google Docs (exported as text)
- Google Sheets (exported as CSV)
- Google Slides (exported as text)
- PDF files
- Plain text files
- And more...

## Usage Example

```
Claude, search my Google Drive for documents about
"quarterly report" and summarize the most recent one.
```

## Permissions

The server requires the following OAuth scopes:
- `https://www.googleapis.com/auth/drive.readonly` - Read file metadata and content
- `https://www.googleapis.com/auth/drive.file` - Access files created by the app
