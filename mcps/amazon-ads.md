---
title: Amazon Ads MCP сервер
description: MCP сервер для доступа к данным Amazon Advertising — кампании Sponsored Products,
  Sponsored Brands, Sponsored Display, отчёты и рекомендации MarketplaceAdPros через
  интеграцию с их платформой.
tags:
- API
- Analytics
- Integration
- Finance
- Productivity
author: MarketplaceAdPros
featured: false
---

MCP сервер для доступа к данным Amazon Advertising — кампании Sponsored Products, Sponsored Brands, Sponsored Display, отчёты и рекомендации MarketplaceAdPros через интеграцию с их платформой.

## Установка

### NPX

```bash
npx @marketplaceadpros/amazon-ads-mcp-server
```

### Из исходников

```bash
npm install
npm run build
```

### Streamable HTTP

```bash
https://app.marketplaceadpros.com/mcp
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "marketplaceadpros": {
      "command": "npx",
      "args": [
        "@marketplaceadpros/amazon-ads-mcp-server"
      ],
      "env": {
        "BEARER_TOKEN": "abcdefghijklmnop"
      }
    }
  }
}
```

### Claude Desktop (локальная сборка)

```json
{
  "mcpServers": {
    "marketplaceadpros": {
      "command": "node",
      "args": [
        "/path/to/amazon-ads-mcp-server/build/index.js"
      ],
      "env": {
        "BEARER_TOKEN": "abcdefghijklmnop"
      }
    }
  }
}
```

### Streamable HTTP MCP

```json
{
  "mcpServers": {
    "marketplaceadpros": {
      "type": "streamable-http",
      "url": "https://app.marketplaceadpros.com/mcp"
    }
  }
}
```

### LibreChat

```json
MAP:
  type: streamable-http
  url: https://app.marketplaceadpros.com/mcp
  headers:
    Authorization: "Bearer abcdefghijklmnop"
```

## Возможности

- Доступ к рекламным ресурсам Sponsored Products, Sponsored Brands и Sponsored Display
- Управление кампаниями, группами объявлений, ключевыми словами, продуктовой рекламой и таргетингом
- Отчёты и возможность запросов на простом английском языке
- Рекомендации и эксперименты MarketplaceAdPros (по подписке)
- Доступен как локальный MCP сервер и как streamable HTTP эндпоинт

## Переменные окружения

### Обязательные
- `BEARER_TOKEN` — Bearer токен, полученный от MarketplaceAdPros.com

## Ресурсы

- [GitHub Repository](https://github.com/MarketplaceAdPros/amazon-ads-mcp-server)

## Примечания

Требуется интеграция с аккаунтом MarketplaceAdPros. Доступен как локальный MCP сервер и как streamable HTTP MCP сервер. Для отладки используйте MCP Inspector с командой 'npm run inspector'.
