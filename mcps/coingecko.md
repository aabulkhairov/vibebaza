---
title: CoinGecko MCP
description: Official CoinGecko MCP server for real-time cryptocurrency market data,
  prices, trends, and onchain analytics.
tags:
- Cryptocurrency
- Finance
- Market Data
- Trading
- Analytics
author: CoinGecko
featured: true
install_command: claude mcp add --transport http coingecko https://mcp.api.coingecko.com/mcp
connection_type: sse
paid_api: true
---

The CoinGecko MCP Server provides AI agents with access to comprehensive cryptocurrency market data, including real-time prices, market trends, onchain analytics, and historical data for 15,000+ coins across 1,000+ exchanges.

## Installation

### Remote Server (Free, No API Key)

```bash
claude mcp add --transport http coingecko https://mcp.api.coingecko.com/mcp
```

### With API Key (Higher Limits)

```bash
claude mcp add --transport http coingecko https://mcp.pro-api.coingecko.com/mcp
```

## Configuration

### Public Server (Keyless)

```json
{
  "mcpServers": {
    "coingecko_mcp": {
      "command": "npx",
      "args": ["mcp-remote", "https://mcp.api.coingecko.com/mcp"]
    }
  }
}
```

### Pro Server (API Key Required)

```json
{
  "mcpServers": {
    "coingecko_mcp": {
      "command": "npx",
      "args": ["mcp-remote", "https://mcp.pro-api.coingecko.com/mcp"]
    }
  }
}
```

### Local Server

```json
{
  "mcpServers": {
    "coingecko_mcp_local": {
      "command": "npx",
      "args": ["-y", "@coingecko/coingecko-mcp"],
      "env": {
        "COINGECKO_PRO_API_KEY": "YOUR_API_KEY",
        "COINGECKO_ENVIRONMENT": "pro"
      }
    }
  }
}
```

## Features

- **Real-time Market Data** - Prices, market cap, and volume for 15,000+ coins
- **Onchain Analytics** - DEX price and liquidity data for 8M+ tokens
- **Market Trends** - Trending coins, gainers, losers, new listings
- **Rich Metadata** - Descriptions, logos, social links, contract addresses
- **Historical Data** - Price and OHLCV data history
- **NFT Data** - Floor prices and collection statistics

## Server Options

| Type | Best For | Rate Limits |
|------|----------|-------------|
| Public (Keyless) | Testing, basic queries | Shared limits |
| Pro (BYOK) | Production apps | 500+ calls/min |
| Local | Development | Based on API plan |

## Usage Examples

```
What is the current price of Bitcoin in USD?
```

```
What are the top 3 trending coins on CoinGecko right now?
```

```
Show me the top 10 cryptocurrencies by market cap with 24h change
```

```
Generate a 30-day price chart for Ethereum
```

## Resources

- [CoinGecko MCP Documentation](https://docs.coingecko.com/docs/mcp-server)
- [API Pricing](https://www.coingecko.com/en/api/pricing)
- [NPM Package](https://www.npmjs.com/package/@coingecko/coingecko-mcp)
