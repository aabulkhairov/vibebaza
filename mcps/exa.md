---
title: Exa MCP
description: Official Exa MCP server for AI-powered web search, code context, deep
  research, and content crawling.
tags:
- Search
- Web
- AI
- Research
- Code
author: Exa
featured: true
install_command: claude mcp add exa -e EXA_API_KEY=your_key -- npx -y exa-mcp-server
connection_type: stdio
paid_api: true
---

The Exa MCP Server connects AI assistants to Exa AI's powerful search capabilities, including web search, research tools, code search, and deep research features.

## Installation

### Remote Server (Recommended)

```bash
claude mcp add --transport http exa https://mcp.exa.ai/mcp
```

### Local Installation

```bash
npm install -g exa-mcp-server
```

### Claude Code

```bash
claude mcp add exa -e EXA_API_KEY=YOUR_API_KEY -- npx -y exa-mcp-server
```

## Configuration

### Remote MCP (Cursor/Claude Code)

```json
{
  "mcpServers": {
    "exa": {
      "type": "http",
      "url": "https://mcp.exa.ai/mcp",
      "headers": {}
    }
  }
}
```

### Local Installation

```json
{
  "mcpServers": {
    "exa": {
      "command": "npx",
      "args": ["-y", "exa-mcp-server"],
      "env": {
        "EXA_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Available Tools

- **web_search_exa** - Real-time web searches with optimized results
- **deep_search_exa** - Deep web search with smart query expansion
- **get_code_context_exa** - Search code snippets, docs, and examples
- **crawling_exa** - Extract content from specific URLs
- **company_research_exa** - Comprehensive company research
- **linkedin_search_exa** - Search LinkedIn for companies and people
- **deep_researcher_start** - Start AI-powered deep research
- **deep_researcher_check** - Check research task status

## Features

- **Exa Code** - Fast, efficient web context for coding agents
- **Deep Research** - AI researcher for complex questions
- **Real-time Search** - Access to billions of indexed pages
- **Code Context** - Find documentation and implementation examples

## Tool Selection

Enable specific tools using the `tools` parameter:

```
https://mcp.exa.ai/mcp?tools=web_search_exa,get_code_context_exa
```

Or enable all tools:

```
https://mcp.exa.ai/mcp?tools=web_search_exa,deep_search_exa,get_code_context_exa,crawling_exa,company_research_exa,linkedin_search_exa,deep_researcher_start,deep_researcher_check
```

## Usage Examples

```
Search for the latest AI research papers
```

```
Find code examples for using the Vercel AI SDK
```

```
Research company information about Anthropic
```

## Resources

- [GitHub Repository](https://github.com/exa-labs/exa-mcp-server)
- [Exa Documentation](https://docs.exa.ai/reference/exa-mcp)
- [NPM Package](https://www.npmjs.com/package/exa-mcp-server)
- [Smithery](https://smithery.ai/server/exa)
