---
title: Puppeteer MCP
description: Browser automation using Puppeteer for web scraping, screenshots, and
  automated interactions.
tags:
- Browser
- Automation
- Screenshots
- Web Scraping
- Testing
author: Anthropic
featured: true
install_command: claude mcp add puppeteer -- npx -y @modelcontextprotocol/server-puppeteer
connection_type: stdio
paid_api: false
---

The Puppeteer MCP server enables browser automation through Puppeteer, allowing Claude to navigate websites, take screenshots, interact with web elements, and extract content.

## Installation

```bash
npm install -g @modelcontextprotocol/server-puppeteer
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-puppeteer"]
    }
  }
}
```

### With Custom Browser Path

```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-puppeteer"],
      "env": {
        "PUPPETEER_EXECUTABLE_PATH": "/path/to/chrome"
      }
    }
  }
}
```

## Available Tools

### puppeteer_navigate
Navigate to a URL.

```typescript
puppeteer_navigate(url: string): NavigationResult
```

### puppeteer_screenshot
Take a screenshot of the current page or element.

```typescript
puppeteer_screenshot(options?: ScreenshotOptions): Screenshot
```

**Options:**
- `name` - Screenshot identifier
- `selector` - CSS selector for element screenshot
- `fullPage` - Capture full scrollable page

### puppeteer_click
Click on an element.

```typescript
puppeteer_click(selector: string): ClickResult
```

### puppeteer_fill
Fill in a form field.

```typescript
puppeteer_fill(selector: string, value: string): FillResult
```

### puppeteer_select
Select an option from a dropdown.

```typescript
puppeteer_select(selector: string, value: string): SelectResult
```

### puppeteer_hover
Hover over an element.

```typescript
puppeteer_hover(selector: string): HoverResult
```

### puppeteer_evaluate
Execute JavaScript in the page context.

```typescript
puppeteer_evaluate(script: string): EvaluationResult
```

## Features

- Headless and headed browser modes
- Screenshot capture (viewport or full page)
- Form interaction (click, fill, select)
- JavaScript execution in page context
- Network request interception
- PDF generation

## Usage Example

```
Claude, navigate to https://example.com, take a screenshot,
then fill in the search form with "MCP servers" and submit it.
```

## Use Cases

- Web scraping and data extraction
- Automated testing
- Screenshot documentation
- Form automation
- Visual regression testing
