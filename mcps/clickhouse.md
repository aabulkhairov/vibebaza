---
title: ClickHouse MCP
description: Connect ClickHouse analytics database to AI assistants for SQL queries,
  schema inspection, and data analysis.
tags:
- Database
- Analytics
- SQL
- ClickHouse
- OLAP
author: ClickHouse
featured: true
install_command: claude mcp add clickhouse -e CLICKHOUSE_HOST=localhost -e CLICKHOUSE_USER=default
  -e CLICKHOUSE_PASSWORD=password -- uvx mcp-clickhouse
connection_type: sse
paid_api: false
---

The ClickHouse MCP server connects ClickHouse databases to AI assistants, enabling SQL query execution, schema inspection, and data analysis with read-only safety guarantees.

## Installation

```bash
pip install mcp-clickhouse
# or
uvx mcp-clickhouse
```

## Configuration

```json
{
  "mcpServers": {
    "mcp-clickhouse": {
      "command": "uvx",
      "args": ["mcp-clickhouse"],
      "env": {
        "CLICKHOUSE_HOST": "your-host",
        "CLICKHOUSE_PORT": "8443",
        "CLICKHOUSE_USER": "your-user",
        "CLICKHOUSE_PASSWORD": "your-password",
        "CLICKHOUSE_SECURE": "true",
        "CLICKHOUSE_VERIFY": "true"
      }
    }
  }
}
```

### ClickHouse Cloud

```json
{
  "env": {
    "CLICKHOUSE_HOST": "your-instance.clickhouse.cloud",
    "CLICKHOUSE_USER": "default",
    "CLICKHOUSE_PASSWORD": "your-password"
  }
}
```

### SQL Playground (Demo)

```json
{
  "env": {
    "CLICKHOUSE_HOST": "sql-clickhouse.clickhouse.com",
    "CLICKHOUSE_USER": "demo",
    "CLICKHOUSE_PASSWORD": ""
  }
}
```

## Available Tools

### ClickHouse Tools
- `run_select_query` - Execute SQL queries (readonly=1 for safety)
- `list_databases` - List all databases
- `list_tables` - List tables with pagination and filtering

### chDB Tools
- `run_chdb_select_query` - Query using embedded ClickHouse engine

## Features

- **Read-Only Safety** - All queries run with `readonly = 1`
- **Pagination Support** - `list_tables` supports `page_token` and `page_size`
- **LIKE Filtering** - Filter tables with `like` or `not_like` patterns
- **Column Metadata** - Optional detailed column information
- **chDB Support** - Embedded ClickHouse for local querying
- **Health Check** - `/health` endpoint for HTTP/SSE transport

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `CLICKHOUSE_HOST` | Server hostname | required |
| `CLICKHOUSE_USER` | Username | required |
| `CLICKHOUSE_PASSWORD` | Password | required |
| `CLICKHOUSE_PORT` | Port number | 8443 (HTTPS) |
| `CLICKHOUSE_SECURE` | Enable HTTPS | true |
| `CLICKHOUSE_VERIFY` | Verify SSL certs | true |
| `CLICKHOUSE_DATABASE` | Default database | none |
| `CHDB_ENABLED` | Enable chDB | false |
| `CHDB_DATA_PATH` | chDB data path | :memory: |

## Usage Example

```
Claude, list all tables in the analytics database and then
run a query to show the top 10 users by total purchases
in the last 30 days.
```

## Resources

- [ClickHouse Documentation](https://clickhouse.com/docs)
- [chDB Documentation](https://github.com/chdb-io/chdb)
