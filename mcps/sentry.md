---
title: Sentry MCP
description: Sentry.io integration for error tracking, issue management, and application
  monitoring.
tags:
- Sentry
- Error Tracking
- Monitoring
- Issues
- Debugging
author: Sentry
featured: true
install_command: claude mcp add sentry -e SENTRY_AUTH_TOKEN=your_token -- uvx mcp-server-sentry
connection_type: stdio
paid_api: true
---

The Sentry MCP server provides integration with Sentry.io for error tracking and application monitoring. It enables Claude to view issues, analyze errors, and help with debugging.

## Installation

Using uvx (recommended):
```bash
uvx mcp-server-sentry
```

Using pip:
```bash
pip install mcp-server-sentry
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "sentry": {
      "command": "uvx",
      "args": ["mcp-server-sentry"],
      "env": {
        "SENTRY_AUTH_TOKEN": "your_auth_token_here"
      }
    }
  }
}
```

## Getting an Auth Token

1. Log in to [Sentry.io](https://sentry.io/)
2. Go to Settings → Auth Tokens
3. Create a new token with the following scopes:
   - `project:read`
   - `issue:read`
   - `event:read`
   - `org:read`

## Available Tools

### list_organizations
List all organizations you have access to.

```typescript
list_organizations(): OrganizationList
```

### list_projects
List projects in an organization.

```typescript
list_projects(organization_slug: string): ProjectList
```

### list_issues
List issues for a project.

```typescript
list_issues(
  organization_slug: string,
  project_slug: string,
  query?: string
): IssueList
```

### get_issue
Get detailed information about an issue.

```typescript
get_issue(issue_id: string): IssueDetails
```

### get_issue_events
Get events associated with an issue.

```typescript
get_issue_events(issue_id: string): EventList
```

### resolve_issue
Resolve an issue.

```typescript
resolve_issue(issue_id: string): ResolveResult
```

## Features

- View unresolved issues
- Analyze error stack traces
- See error frequency and impact
- Track issue status and assignments
- Access event details and breadcrumbs

## Usage Example

```
Claude, show me the most recent unresolved issues in our
production project and analyze the top error's stack trace.
```

## Use Cases

- Debugging production errors
- Prioritizing bug fixes
- Understanding error patterns
- Monitoring application health
- Investigating user-reported issues
