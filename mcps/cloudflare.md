---
title: Cloudflare MCP
description: Deploy, configure, and manage Cloudflare resources including Workers,
  KV, R2, D1, and more.
tags:
- Cloudflare
- Workers
- Edge
- Serverless
- CDN
author: Cloudflare
featured: true
install_command: claude mcp add cloudflare -- npx mcp-remote https://bindings.mcp.cloudflare.com/mcp
connection_type: sse
paid_api: true
---

The Cloudflare MCP server enables interaction with Cloudflare's developer platform, allowing you to deploy, configure, and manage resources across Workers, KV, R2, D1, and other Cloudflare services.

## Available Servers

Cloudflare provides multiple specialized MCP servers:

| Server | Description | URL |
|--------|-------------|-----|
| Documentation | Get up-to-date Cloudflare reference information | `https://docs.mcp.cloudflare.com/mcp` |
| Workers Bindings | Build Workers with storage, AI, and compute | `https://bindings.mcp.cloudflare.com/mcp` |
| Workers Builds | Manage Cloudflare Workers Builds | `https://builds.mcp.cloudflare.com/mcp` |
| Observability | Debug and analyze logs and analytics | `https://observability.mcp.cloudflare.com/mcp` |
| Radar | Global Internet traffic insights and URL scans | `https://radar.mcp.cloudflare.com/mcp` |
| Container | Spin up sandbox development environments | `https://containers.mcp.cloudflare.com/mcp` |
| Browser Rendering | Fetch web pages and take screenshots | `https://browser.mcp.cloudflare.com/mcp` |
| AI Gateway | Search logs, inspect prompts and responses | `https://ai-gateway.mcp.cloudflare.com/mcp` |

## Configuration

Since these are remote MCP servers, use `mcp-remote`:

```json
{
  "mcpServers": {
    "cloudflare-bindings": {
      "command": "npx",
      "args": ["mcp-remote", "https://bindings.mcp.cloudflare.com/mcp"]
    },
    "cloudflare-observability": {
      "command": "npx",
      "args": ["mcp-remote", "https://observability.mcp.cloudflare.com/mcp"]
    }
  }
}
```

## Features

- Deploy and manage Workers
- Interact with KV namespaces
- Manage R2 object storage
- Query D1 databases
- View logs and analytics
- Access Cloudflare Radar data
- Browser automation and screenshots

## Authentication

Authentication is handled through Cloudflare OAuth when connecting to the remote servers. You'll be prompted to authorize access to your Cloudflare account.

## Usage Example

```
Claude, deploy a new Worker to handle API requests,
create a KV namespace for caching, and bind them together.
```

## Supported Transports

- `streamable-http` via `/mcp` endpoint
- `sse` (deprecated) via `/sse` endpoint

## Note

Some features may require a paid Cloudflare Workers plan. Ensure your account has the necessary subscription for the features you intend to use.
