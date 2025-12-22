---
title: Axiom MCP
description: Query and analyze your Axiom logs, traces, and all other event data in
  natural language using APL.
tags:
- Observability
- Logging
- Analytics
- Monitoring
- DevOps
author: Axiom
featured: true
install_command: claude mcp add --transport http axiom https://mcp.axiom.co
connection_type: stdio
paid_api: false
---

Axiom MCP Server enables AI agents to query and analyze your logs, traces, and event data using natural language through Axiom's Processing Language (APL).

## Installation

### Remote Server (Recommended)

Axiom hosts a remote MCP server:

```bash
claude mcp add --transport http axiom https://mcp.axiom.co
```

## Configuration

### Remote MCP Server

```json
{
  "mcpServers": {
    "axiom": {
      "type": "http",
      "url": "https://mcp.axiom.co"
    }
  }
}
```

## Available Tools

- `queryApl` - Execute APL queries against Axiom datasets
- `listDatasets` - List available Axiom datasets
- `getDatasetSchema` - Get dataset schema
- `getSavedQueries` - Retrieve saved/starred APL queries
- `getMonitors` - List monitoring configurations
- `getMonitorsHistory` - Get monitor execution history

## Features

- **Natural Language Queries** - Query your data conversationally
- **APL Support** - Full Axiom Processing Language capabilities
- **Real-time Analysis** - Analyze logs and traces in real-time
- **Monitor Management** - Access and manage monitoring configurations

## Usage Examples

```
What errors occurred in the last hour?
```

```
Show me the top 10 slowest API endpoints
```

```
List all datasets in my Axiom account
```

## Resources

- [Axiom Documentation](https://axiom.co/docs)
- [APL Reference](https://axiom.co/docs/apl/introduction)
