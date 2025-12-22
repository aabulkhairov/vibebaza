---
title: MCP STDIO to Streamable HTTP Adapter MCP сервер
description: Адаптер, который позволяет MCP клиентам с поддержкой только STDIO подключаться к Streamable HTTP MCP серверам, создавая мост между различными транспортными протоколами.
tags:
- Integration
- API
- Productivity
author: pyroprompts
featured: false
---

Адаптер, который позволяет MCP клиентам с поддержкой только STDIO подключаться к Streamable HTTP MCP серверам, создавая мост между различными транспортными протоколами.

## Установка

### NPX

```bash
npx @pyroprompts/mcp-stdio-to-streamable-http-adapter
```

### Из исходного кода

```bash
npm install
npm run build
node /path/to/mcp-stdio-to-streamable-http-adapter/build/index.js
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "my-saas-app-development": {
      "command": "npx",
      "args": [
        "@pyroprompts/mcp-stdio-to-streamable-http-adapter"
      ],
      "env": {
        "URI": "http://localhost:3002/mcp",
        "MCP_NAME": "local-custom-streamable-http-adapter"
      }
    }
  }
}
```

### Claude Desktop (Собранный)

```json
{
  "mcpServers": {
    "my-saas-app-development": {
      "command": "node",
      "args": [
        "/path/to/mcp-stdio-to-streamable-http-adapter/build/index.js"
      ],
      "env": {
        "URI": "http://localhost:3002/mcp",
        "MCP_NAME": "local-custom-streamable-http-adapter"
      }
    }
  }
}
```

### LibreChat

```json
my-saas-app-development:
  type: stdio
  command: npx
  args:
    - -y
    - @pyroprompts/mcp-stdio-to-streamable-http-adapter
  env:
    URI: "http://localhost:3002/mcp"
    MCP_NAME: "my-custom-saas-app"
    PATH: '/usr/local/bin:/usr/bin:/bin'
```

## Возможности

- Мост между STDIO MCP клиентами и Streamable HTTP MCP серверами
- Поддержка аутентификации с Bearer токеном
- Поддержка конфигурации нескольких серверов
- Пользовательское именование серверов
- Работает с Claude Desktop и LibreChat

## Переменные окружения

### Обязательные
- `URI` - URL Streamable HTTP MCP сервера

### Опциональные
- `MCP_NAME` - Имя MCP сервера (обязательно при конфигурации нескольких серверов)
- `BEARER_TOKEN` - Bearer токен для аутентификации на Streamable HTTP MCP сервере

## Ресурсы

- [GitHub Repository](https://github.com/pyroprompts/mcp-stdio-to-streamable-http-adapter)

## Примечания

Этот адаптер решает проблему отставания поддержки клиентов для нового транспортного протокола Streamable HTTP, введенного в марте 2025 года. Он позволяет разработчикам создавать Streamable HTTP MCP серверы, сохраняя совместимость с существующими клиентами, поддерживающими только STDIO.