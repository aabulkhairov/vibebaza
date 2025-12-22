---
title: Windsor MCP сервер
description: Windsor MCP позволяет вашей LLM запрашивать, исследовать и анализировать все бизнес-данные, интегрированные в Windsor.ai, без написания SQL или кастомных скриптов. Сервер легко подключается к 325+ платформам, предоставляя AI-инструментам доступ в реальном времени к данным по перформанс-маркетингу, продажам и клиентам.
tags:
- Analytics
- Integration
- API
- CRM
- Database
author: windsor-ai
featured: false
---

Windsor MCP позволяет вашей LLM запрашивать, исследовать и анализировать все бизнес-данные, интегрированные в Windsor.ai, без написания SQL или кастомных скриптов. Сервер легко подключается к 325+ платформам, предоставляя AI-инструментам доступ в реальном времени к данным по перформанс-маркетингу, продажам и клиентам.

## Установка

### MCP Proxy

```bash
uv tool install mcp-proxy
which mcp-proxy  # Copy full path
```

### Gemini CLI

```bash
npm install -g @google/gemini-cli
```

## Конфигурация

### Claude Desktop Developer Proxy

```json
{
  "mcpServers": {
    "windsor": {
      "command": "/Users/{your-username}/.local/bin/mcp-proxy",
      "args": ["https://mcp.windsor.ai/sse"]
    }
  }
}
```

### Cursor Desktop

```json
{
  "mcpServers": {
    "windsor": {
      "command": "/Users/{your-username}/.local/bin/mcp-proxy",
      "args": ["https://mcp.windsor.ai/sse"]
    }
  }
}
```

### Gemini CLI

```json
{
  "mcpServers": {
    "windsor": {
      "command": "/Users/{your-username}/.local/bin/mcp-proxy",
      "args": ["https://mcp.windsor.ai/sse"]
    }
  }
}
```

## Возможности

- Доступ к бизнес-данным на естественном языке
- Готовая интеграция с 325+ источниками, включая Facebook Ads, GA4, HubSpot, Salesforce, Shopify, TikTok Ads
- Настройка без кода через Claude Desktop или легковесный dev proxy
- Совместимость с открытыми стандартами Claude, Perplexity, Cursor и другими
- Аналитика в реальном времени без SQL
- Прямая интеграция в интерфейс чата LLM

## Примеры использования

```
What campaigns had the best ROAS last month?
```

```
Give me a breakdown of spend by channel over the past 90 days.
```

```
What campaigns are wasting our advertising budget?
```

```
What was total ad spend by channel last month?
```

```
Break down ROAS for Meta vs Google Ads for Q2
```

## Ресурсы

- [GitHub Repository](https://github.com/windsor-ai/windsor_mcp)

## Примечания

Windsor MCP находится в стадии бета-тестирования. Требуется аккаунт Windsor.ai с интегрированными данными и доступом к API ключу. Внешние коннекторы Claude Desktop доступны только на платных планах. Для прямого подключения Claude Desktop используйте URLs: https://mcp.windsor.ai или https://mcp.windsor.ai/sse. Для аутентификации требуется Windsor API ключ.