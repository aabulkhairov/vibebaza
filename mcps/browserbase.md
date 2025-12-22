---
title: Browserbase MCP
description: Cloud browser automation with Stagehand for AI-powered web interactions,
  screenshots, and data extraction.
tags:
- Browser
- Automation
- Web Scraping
- Playwright
- Stagehand
author: Browserbase
featured: true
install_command: claude mcp add browserbase -e BROWSERBASE_API_KEY=your_key -e BROWSERBASE_PROJECT_ID=your_project
  -e GEMINI_API_KEY=your_gemini_key -- npx -y @browserbasehq/mcp-server-browserbase
connection_type: stdio
paid_api: true
---

The Browserbase MCP server provides cloud browser automation capabilities using Browserbase and Stagehand. It enables LLMs to interact with web pages, take screenshots, extract information, and perform automated actions with atomic precision.

## Installation

```bash
npm install -g @browserbasehq/mcp-server-browserbase
```

## Configuration

### Remote Server (Recommended)

Get a hosted URL from [Smithery](https://smithery.ai/server/@browserbasehq/mcp-browserbase) with LLM costs included:

```json
{
  "mcpServers": {
    "browserbase": {
      "type": "http",
      "url": "your-smithery-url.com"
    }
  }
}
```

### Local Server

```json
{
  "mcpServers": {
    "browserbase": {
      "command": "npx",
      "args": ["@browserbasehq/mcp-server-browserbase"],
      "env": {
        "BROWSERBASE_API_KEY": "your-api-key",
        "BROWSERBASE_PROJECT_ID": "your-project-id",
        "GEMINI_API_KEY": "your-gemini-key"
      }
    }
  }
}
```

## Features

| Feature | Description |
|---------|-------------|
| Browser Automation | Control cloud browsers via Browserbase |
| Data Extraction | Extract structured data from any webpage |
| Web Interaction | Navigate, click, and fill forms |
| Screenshots | Full-page and element screenshots |
| Model Flexibility | Supports OpenAI, Claude, Gemini, and more |
| Vision Support | Annotated screenshots for complex DOMs |
| Session Management | Create, manage, and close browser sessions |
| High Performance | 20-40% faster with automatic caching (v3) |

## Stagehand v3 Features

- Targeted extraction across iframes and shadow roots
- CSS selector support with improved element targeting
- Multi-browser support (Playwright, Puppeteer, Patchright)
- Built-in primitives: `page`, `locator`, `frameLocator`, `deepLocator`
- Experimental features with `--experimental` flag

## Configuration Options

| Flag | Description |
|------|-------------|
| `--proxies` | Enable Browserbase proxies |
| `--advancedStealth` | Enable advanced stealth mode (Scale Plan) |
| `--keepAlive` | Enable keep-alive sessions |
| `--contextId` | Specify a Browserbase Context ID |
| `--browserWidth` | Viewport width (default: 1024) |
| `--browserHeight` | Viewport height (default: 768) |
| `--modelName` | AI model (default: gemini-2.0-flash) |
| `--experimental` | Enable experimental features |

## Usage Example

```
Claude, navigate to example.com, take a screenshot,
and extract all product prices from the page.
```

## Resources

- [Browserbase Documentation](https://docs.browserbase.com/)
- [Stagehand Documentation](https://docs.stagehand.dev/)
