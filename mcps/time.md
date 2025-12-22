---
title: Time MCP
description: Time and timezone conversion utilities for getting current time and converting
  between timezones.
tags:
- Time
- Timezone
- Utilities
- Official
author: Anthropic
featured: false
install_command: claude mcp add time -- uvx mcp-server-time
connection_type: stdio
paid_api: false
---

The Time MCP server provides tools for getting the current time and converting between timezones. It's useful for scheduling, time-sensitive operations, and working across different regions.

## Installation

Using uvx (recommended):
```bash
uvx mcp-server-time
```

Using pip:
```bash
pip install mcp-server-time
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "time": {
      "command": "uvx",
      "args": ["mcp-server-time"]
    }
  }
}
```

### With Local Timezone

```json
{
  "mcpServers": {
    "time": {
      "command": "uvx",
      "args": ["mcp-server-time", "--local-timezone", "America/New_York"]
    }
  }
}
```

## Available Tools

### get_current_time
Get the current time in a specific timezone.

```typescript
get_current_time(timezone?: string): TimeResult
```

**Parameters:**
- `timezone` - IANA timezone name (e.g., "America/New_York", "Europe/London")

**Returns:**
- Current time in the specified timezone
- ISO 8601 formatted datetime
- Timezone offset information

### convert_time
Convert time between timezones.

```typescript
convert_time(
  source_timezone: string,
  time: string,
  target_timezone: string
): ConversionResult
```

**Parameters:**
- `source_timezone` - Source IANA timezone
- `time` - Time to convert (ISO 8601 format)
- `target_timezone` - Target IANA timezone

## Supported Timezones

Uses IANA timezone database. Common examples:
- `America/New_York` - Eastern Time
- `America/Los_Angeles` - Pacific Time
- `Europe/London` - GMT/BST
- `Europe/Paris` - Central European Time
- `Asia/Tokyo` - Japan Standard Time
- `Asia/Shanghai` - China Standard Time
- `Australia/Sydney` - Australian Eastern Time

## Usage Example

```
Claude, what time is it in Tokyo right now?
Also, if it's 3pm in New York, what time is that in London?
```
