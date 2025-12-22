---
title: PostgreSQL MCP
description: MCP server for PostgreSQL database operations with schema inspection
  and query execution.
tags:
- PostgreSQL
- Database
- SQL
- Official
author: Anthropic
featured: true
install_command: claude mcp add postgres -- npx -y @modelcontextprotocol/server-postgres
  postgresql://localhost/mydb
connection_type: stdio
paid_api: false
---

The PostgreSQL MCP server provides Claude with read-only access to PostgreSQL databases for data analysis and schema inspection.

## Installation

```bash
npm install -g @modelcontextprotocol/server-postgres
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://user:password@localhost:5432/database"
      ]
    }
  }
}
```

## Available Tools

### query
Execute a read-only SQL query.

```typescript
query(sql: string): QueryResult
```

**Note**: Only SELECT queries are allowed for safety.

### list_tables
List all tables in the database.

```typescript
list_tables(): TableInfo[]
```

### describe_table
Get schema information for a table.

```typescript
describe_table(table_name: string): ColumnInfo[]
```

## Resources

The server exposes database schema as resources:

- `postgres://schema` - Full database schema
- `postgres://tables/{table_name}` - Individual table schemas

## Security Considerations

- Read-only access by default
- Connection string should use appropriate credentials
- Consider using a read-replica for production
- Limit accessible schemas if needed

## Usage Example

```
Claude, please analyze the users table and show me
the distribution of users by signup month.
```

Claude will:
1. Inspect the table schema
2. Write an appropriate SQL query
3. Execute and present the results
