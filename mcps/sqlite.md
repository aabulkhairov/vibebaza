---
title: SQLite MCP
description: SQLite database operations for querying, analyzing, and managing local
  SQLite databases.
tags:
- Database
- SQLite
- SQL
- Analytics
author: Anthropic
featured: true
install_command: claude mcp add sqlite -- uvx mcp-server-sqlite --db-path /path/to/database.db
connection_type: stdio
paid_api: false
---

The SQLite MCP server provides tools for interacting with SQLite databases, enabling Claude to query data, analyze schemas, and perform database operations.

## Installation

Using uvx (recommended):
```bash
uvx mcp-server-sqlite --db-path /path/to/database.db
```

Using pip:
```bash
pip install mcp-server-sqlite
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "sqlite": {
      "command": "uvx",
      "args": [
        "mcp-server-sqlite",
        "--db-path",
        "/path/to/your/database.db"
      ]
    }
  }
}
```

### Read-Only Mode

```json
{
  "mcpServers": {
    "sqlite": {
      "command": "uvx",
      "args": [
        "mcp-server-sqlite",
        "--db-path",
        "/path/to/database.db",
        "--read-only"
      ]
    }
  }
}
```

## Available Tools

### read_query
Execute a SELECT query and return results.

```typescript
read_query(query: string): QueryResult
```

### write_query
Execute an INSERT, UPDATE, or DELETE query.

```typescript
write_query(query: string): WriteResult
```

### create_table
Create a new table with specified schema.

```typescript
create_table(query: string): CreateResult
```

### list_tables
List all tables in the database.

```typescript
list_tables(): TableList
```

### describe_table
Get schema information for a table.

```typescript
describe_table(table_name: string): TableSchema
```

### append_insight
Add a business insight to the memo.

```typescript
append_insight(insight: string): void
```

## Features

- Read and write operations
- Schema inspection
- Safe parameterized queries
- Transaction support
- Read-only mode for safety
- Business insight memos

## Usage Example

```
Claude, connect to my database and show me all tables.
Then query the users table to find all active users
created in the last month.
```

## Security

- Use read-only mode for untrusted databases
- Parameterized queries prevent SQL injection
- File-level access permissions apply
