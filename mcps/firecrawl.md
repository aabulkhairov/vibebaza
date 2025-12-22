---
title: Firecrawl MCP
description: Official Firecrawl MCP server for powerful web scraping, crawling, search,
  and structured data extraction.
tags:
- Web Scraping
- Crawling
- Search
- Data Extraction
- AI
author: Firecrawl
featured: true
install_command: claude mcp add firecrawl -e FIRECRAWL_API_KEY=your_key -- npx -y
  firecrawl-mcp
connection_type: stdio
paid_api: true
---

The Firecrawl MCP Server provides powerful web scraping capabilities for AI assistants, including single page scraping, batch operations, site crawling, and structured data extraction.

## Installation

### NPX

```bash
env FIRECRAWL_API_KEY=fc-YOUR_API_KEY npx -y firecrawl-mcp
```

### Global Installation

```bash
npm install -g firecrawl-mcp
```

## Configuration

### Claude Desktop

```json
{
  "mcpServers": {
    "firecrawl-mcp": {
      "command": "npx",
      "args": ["-y", "firecrawl-mcp"],
      "env": {
        "FIRECRAWL_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

### Cursor

1. Open Cursor Settings
2. Go to Features > MCP Servers
3. Add the configuration above

## Available Tools

| Tool | Best For | Returns |
|------|----------|---------|
| `firecrawl_scrape` | Single page content | markdown/html |
| `firecrawl_batch_scrape` | Multiple known URLs | markdown/html[] |
| `firecrawl_map` | Discovering URLs on a site | URL[] |
| `firecrawl_crawl` | Multi-page extraction | markdown/html[] |
| `firecrawl_search` | Web search for info | results[] |
| `firecrawl_extract` | Structured data from pages | JSON |

## Features

- **Web Scraping** - Extract content from any webpage
- **Batch Processing** - Scrape multiple URLs efficiently
- **Site Crawling** - Discover and crawl entire websites
- **Search** - Search the web and extract content
- **Structured Extraction** - Extract data using schemas
- **Automatic Retries** - Built-in rate limiting and retries

## Environment Variables

### Required
- `FIRECRAWL_API_KEY` - Your Firecrawl API key

### Optional
- `FIRECRAWL_API_URL` - Custom API endpoint for self-hosted
- `FIRECRAWL_RETRY_MAX_ATTEMPTS` - Max retry attempts (default: 3)
- `FIRECRAWL_RETRY_INITIAL_DELAY` - Initial retry delay in ms (default: 1000)

## Usage Examples

```
Scrape the content from https://example.com
```

```
Search for the latest AI news and extract the content
```

```
Extract product information from these e-commerce URLs
```

## Resources

- [GitHub Repository](https://github.com/firecrawl/firecrawl-mcp-server)
- [Firecrawl Documentation](https://docs.firecrawl.dev/)
- [API Pricing](https://www.firecrawl.dev/pricing)
- [Smithery](https://smithery.ai/server/@mendableai/mcp-server-firecrawl)
