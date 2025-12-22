---
title: Routine MCP сервер
description: MCP сервер для приложения Routine, который обеспечивает взаимодействие с календарями, задачами, заметками и другими функциями продуктивности через Model Context Protocol.
tags:
- Productivity
- Integration
- API
author: routineco
featured: false
---

MCP сервер для приложения Routine, который обеспечивает взаимодействие с календарями, задачами, заметками и другими функциями продуктивности через Model Context Protocol.

## Установка

### NPX

```bash
npx routine-mcp-server
```

### Из исходного кода

```bash
yarn
yarn build
```

## Конфигурация

### Claude Desktop (продакшен)

```json
{
  "mcpServers": {
    "routine": {
      "command": "npx",
      "args": ["routine-mcp-server"]
    }
  }
}
```

### Claude Desktop (разработка)

```json
{
  "mcpServers": {
    "routine": {
      "command": "/absolute/path/to/bin/node",
      "args": ["/absolute/path/to/mcp-server/dist/index.js"]
    }
  }
}
```

## Ресурсы

- [GitHub Repository](https://github.com/routineco/mcp-server)

## Примечания

Для работы MCP сервера требуется запущенное приложение Routine. Сервер взаимодействует через stdin/stdout, следуя протоколу MCP.