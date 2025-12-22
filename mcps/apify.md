---
title: Apify MCP
description: Extract data from websites using thousands of ready-made scrapers, crawlers,
  and automation tools from Apify Store.
tags:
- Web Scraping
- Data Extraction
- Automation
- Crawlers
author: Apify
featured: true
install_command: claude mcp add apify -e APIFY_TOKEN=your_token -- npx -y @apify/actors-mcp-server
connection_type: stdio
paid_api: true
---

The Apify MCP server enables AI agents to extract data from social media, search engines, maps, e-commerce sites, or any other website using thousands of ready-made scrapers, crawlers, and automation tools available on the Apify Store.

## Installation

```bash
npm install -g @apify/actors-mcp-server
```

## Configuration

### Remote Server (Recommended)

For the easiest setup, connect to the hosted server with OAuth:

```
https://mcp.apify.com
```

### Local Server

```json
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["-y", "@apify/actors-mcp-server"],
      "env": {
        "APIFY_TOKEN": "your-apify-token"
      }
    }
  }
}
```

## Available Tools

### Actor Tools
- `search-actors` - Search for Actors in the Apify Store
- `fetch-actor-details` - Get detailed information about a specific Actor
- `call-actor` - Call an Actor and get its run results
- `add-actor` - Dynamically add an Actor as a new tool

### Documentation Tools
- `search-apify-docs` - Search the Apify documentation
- `fetch-apify-docs` - Fetch documentation page content

### Storage Tools
- `get-dataset` - Get metadata about a dataset
- `get-dataset-items` - Retrieve items from a dataset
- `get-key-value-store` - Get key-value store metadata
- `get-key-value-store-record` - Get value by key

## Popular Actors

- **Facebook Posts Scraper** - Extract data from Facebook posts
- **Google Maps Email Extractor** - Extract contact details from Google Maps
- **Google Search Results Scraper** - Scrape Google SERPs
- **Instagram Scraper** - Scrape Instagram posts, profiles, and comments
- **RAG Web Browser** - Search and scrape web content for RAG applications

## Features

- Access to 8,000+ pre-built Actors on Apify Store
- Dynamic tool discovery and loading
- Support for multiple AI models (Claude, GPT-4, Gemini)
- OAuth authentication for hosted server
- Comprehensive error handling

## Getting an API Token

Sign up at [Apify](https://apify.com/) and generate an API token from your account settings.

## Usage Example

```
Claude, use the Instagram Scraper to extract the latest 10 posts
from @techcrunch and summarize the main topics.
```
