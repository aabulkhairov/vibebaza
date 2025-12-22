---
title: Chrome DevTools MCP
description: Official Google Chrome DevTools MCP server for browser debugging, automation,
  performance analysis, and network inspection.
tags:
- Browser
- Debugging
- Performance
- Automation
- Google
author: Google Chrome
featured: true
install_command: claude mcp add chrome-devtools -- npx -y chrome-devtools-mcp@latest
connection_type: stdio
paid_api: false
---

The Chrome DevTools MCP Server is the official MCP implementation from the Chrome DevTools team. It enables AI coding assistants to control and inspect a live Chrome browser for reliable automation, in-depth debugging, and performance analysis.

## Installation

```bash
claude mcp add chrome-devtools -- npx -y chrome-devtools-mcp@latest
```

## Configuration

### Claude Code

```bash
claude mcp add chrome-devtools -- npx -y chrome-devtools-mcp@latest
```

### Claude Desktop

```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest"]
    }
  }
}
```

## Key Features

- **Performance Insights** - Record traces and extract actionable performance insights
- **Browser Debugging** - Analyze network requests, console logs, and take screenshots
- **Reliable Automation** - Uses Puppeteer for automated browser interactions
- **Page Snapshots** - Take accessibility tree snapshots for AI-friendly content

## Available Tools

### Input Automation (8 tools)
- `click`, `drag`, `fill`, `fill_form`
- `handle_dialog`, `hover`, `press_key`, `upload_file`

### Navigation (6 tools)
- `close_page`, `list_pages`, `navigate_page`
- `new_page`, `select_page`, `wait_for`

### Performance (3 tools)
- `performance_start_trace`, `performance_stop_trace`
- `performance_analyze_insight`

### Debugging (5 tools)
- `take_screenshot`, `take_snapshot`
- `evaluate_script`, `list_console_messages`, `get_console_message`

### Network (2 tools)
- `list_network_requests`, `get_network_request`

## Configuration Options

| Option | Description |
|--------|-------------|
| `--headless` | Run browser in headless mode |
| `--browserUrl` | Connect to running Chrome instance |
| `--channel` | Chrome channel (stable, canary, beta, dev) |
| `--viewport` | Initial viewport size (e.g., 1280x720) |

## Usage Examples

```
Check the performance of https://example.com
```

```
Take a screenshot of the current page
```

```
List all network requests made by this page
```

## Requirements

- Node.js v20.19+ (latest maintenance LTS)
- Chrome (current stable version)

## Resources

- [GitHub Repository](https://github.com/ChromeDevTools/chrome-devtools-mcp)
- [Tool Reference](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/main/docs/tool-reference.md)
- [Chrome DevTools Blog](https://developer.chrome.com/blog/chrome-devtools-mcp)
