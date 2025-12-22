---
title: Bright Data MCP
description: Give your AI real-time web superpowers with enterprise-grade web scraping,
  browser automation, and anti-blocking technology.
tags:
- Web Scraping
- Data Collection
- Browser Automation
- Proxy
- AI Agents
author: Bright Data
featured: true
install_command: claude mcp add brightdata -e API_TOKEN=your_token -- npx -y @brightdata/mcp
connection_type: stdio
paid_api: true
---

The Bright Data MCP Server is a powerful all-in-one solution for public web access, enabling AI agents to scrape websites, search the web, and automate browsers without getting blocked.

## Installation

### Remote Server (Recommended)

```bash
# Add to Claude Desktop: Settings → Connectors → Add custom connector
# URL: https://mcp.brightdata.com/mcp?token=YOUR_API_TOKEN
```

### Local Installation

```bash
npx -y @brightdata/mcp
```

## Configuration

### Remote Server

```json
{
  "mcpServers": {
    "brightdata": {
      "type": "http",
      "url": "https://mcp.brightdata.com/mcp?token=YOUR_API_TOKEN"
    }
  }
}
```

### Local Server

```json
{
  "mcpServers": {
    "brightdata": {
      "command": "npx",
      "args": ["-y", "@brightdata/mcp"],
      "env": {
        "API_TOKEN": "your-api-token"
      }
    }
  }
}
```

## Pricing & Modes

### Rapid Mode (Free Tier)
- **5,000 requests/month FREE**
- Web Search
- Scraping with Web Unlocker
- Perfect for prototyping

### Pro Mode (Pay-as-you-go)
- Browser Automation
- Web Data APIs
- 60+ Advanced Tools
- Enable with `PRO_MODE=true`

## Available Tools

### Rapid Mode (Free)

| Tool | Description |
|------|-------------|
| `search_engine` | Web search with AI-optimized results |
| `scrape_as_markdown` | Convert any webpage to clean markdown |

### Pro Mode

| Category | Description |
|----------|-------------|
| Browser Control | Full browser automation |
| Web Data APIs | Structured data extraction |
| E-commerce | Amazon, eBay, Walmart data |
| Social Media | Twitter, LinkedIn, Instagram |
| Maps & Local | Google Maps, business data |

## Features

- **Never Gets Blocked** - Enterprise-grade anti-blocking
- **Global Access** - Bypass geo-restrictions automatically
- **Clean Markdown** - AI-ready content extraction
- **Lightning Fast** - Optimized for minimal latency

## Advanced Configuration

```json
{
  "mcpServers": {
    "brightdata": {
      "command": "npx",
      "args": ["-y", "@brightdata/mcp"],
      "env": {
        "API_TOKEN": "your-token",
        "PRO_MODE": "true",
        "RATE_LIMIT": "100/1h",
        "WEB_UNLOCKER_ZONE": "custom"
      }
    }
  }
}
```

## Usage Examples

```
What's Tesla's current stock price?
```

```
Find the best-rated restaurants in Tokyo right now
```

```
Get today's weather forecast for New York
```

## Resources

- [Documentation](https://docs.brightdata.com/mcp-server/overview)
- [GitHub Repository](https://github.com/brightdata/brightdata-mcp)
- [Online Playground](https://brightdata.com/ai/playground-chat)
