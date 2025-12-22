---
title: GitLab MCP
description: GitLab API integration for project management, file operations, merge
  requests, and more.
tags:
- GitLab
- Git
- Issues
- Merge Requests
- CI/CD
author: Anthropic
featured: true
install_command: claude mcp add gitlab -e GITLAB_PERSONAL_ACCESS_TOKEN=your_token
  -- npx -y @modelcontextprotocol/server-gitlab
connection_type: stdio
paid_api: true
---

The GitLab MCP server provides comprehensive integration with GitLab's API, enabling project management, file operations, merge requests, and more.

## Installation

```bash
npm install -g @modelcontextprotocol/server-gitlab
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "gitlab": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-gitlab"],
      "env": {
        "GITLAB_PERSONAL_ACCESS_TOKEN": "your_token_here",
        "GITLAB_API_URL": "https://gitlab.com/api/v4"
      }
    }
  }
}
```

### Self-Hosted GitLab

For self-hosted instances, change `GITLAB_API_URL` to your instance's API endpoint.

## Available Tools

### create_or_update_file
Create or update a single file in a project.

### push_files
Push multiple files in a single commit.

### search_repositories
Search for GitLab projects.

### create_repository
Create a new GitLab project.

### get_file_contents
Get contents of a file or directory.

### create_issue
Create a new issue with title, description, assignees, and labels.

### create_merge_request
Create a new merge request between branches.

### fork_repository
Fork a project to your namespace.

### create_branch
Create a new branch from a source ref.

## Features

- **Automatic Branch Creation**: Branches are created automatically if they don't exist
- **Comprehensive Error Handling**: Clear error messages for common issues
- **Git History Preservation**: Operations maintain proper Git history
- **Batch Operations**: Support for both single-file and multi-file operations

## Authentication

Create a GitLab Personal Access Token with the following scopes:
- `api` - Full API access
- `read_api` - Read-only access
- `read_repository` and `write_repository` - Repository operations

## Usage Example

```
Claude, create a new merge request in my-project from
feature-branch to main with a description of the changes.
```
