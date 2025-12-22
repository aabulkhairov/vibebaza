---
title: Brave Search MCP
description: Web and local search using Brave's Search API with AI-powered summarization,
  image, video, and news search.
tags:
- Search
- Web
- News
- Images
- Videos
- AI
author: Brave
featured: true
install_command: claude mcp add brave-search -e BRAVE_API_KEY=your_api_key -- npx
  -y @brave/brave-search-mcp-server
connection_type: sse
paid_api: true
---

The Brave Search MCP server integrates the Brave Search API, providing comprehensive search capabilities including web search, local business search, image search, video search, news search, and AI-powered summarization.

## Installation

```bash
npm install -g @brave/brave-search-mcp-server
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@brave/brave-search-mcp-server"],
      "env": {
        "BRAVE_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Available Tools

### brave_web_search
Performs comprehensive web searches with rich result types and filtering.

```typescript
brave_web_search(query: string, options?: SearchOptions): SearchResults
```

**Parameters:**
- `query` - Search terms (max 400 chars, 50 words)
- `country` - Country code (default: "US")
- `count` - Results per page (1-20, default: 10)
- `safesearch` - Content filtering ("off", "moderate", "strict")
- `freshness` - Time filter ("pd", "pw", "pm", "py")

### brave_local_search
Searches for local businesses and places with ratings, hours, and descriptions.

```typescript
brave_local_search(query: string, options?: LocalSearchOptions): LocalResults
```

### brave_image_search
Searches for images with metadata and thumbnail information.

```typescript
brave_image_search(query: string, options?: ImageSearchOptions): ImageResults
```

### brave_video_search
Searches for videos with comprehensive metadata.

```typescript
brave_video_search(query: string, options?: VideoSearchOptions): VideoResults
```

### brave_news_search
Searches for current news articles with freshness controls.

```typescript
brave_news_search(query: string, options?: NewsSearchOptions): NewsResults
```

### brave_summarizer
Generates AI-powered summaries from web search results.

```typescript
brave_summarizer(key: string, options?: SummarizerOptions): Summary
```

## Getting an API Key

1. Sign up for a [Brave Search API account](https://brave.com/search/api/)
2. Choose a plan:
   - **Free**: 2,000 queries/month, basic web search
   - **Pro**: Enhanced features including local search, AI summaries
3. Generate your API key from the [developer dashboard](https://api-dashboard.search.brave.com/app/keys)

## Usage Example

```
Claude, search the web for the latest news about AI developments
and summarize the top results.
```
