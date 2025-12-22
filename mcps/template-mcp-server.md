---
title: Template MCP Server MCP сервер
description: CLI инструмент для быстрого создания и настройки новых проектов MCP (Model Context Protocol) серверов с использованием FastMCP фреймворка, поддержкой TypeScript и двумя вариантами транспорта.
tags:
- Code
- Productivity
- DevOps
author: mcpdotdirect
featured: false
---

CLI инструмент для быстрого создания и настройки новых проектов MCP (Model Context Protocol) серверов с использованием FastMCP фреймворка, поддержкой TypeScript и двумя вариантами транспорта.

## Установка

### NPX

```bash
npx @mcpdotdirect/create-mcp-server
```

### NPM Init

```bash
npm init @mcpdotdirect/mcp-server
```

## Конфигурация

### Конфигурация Cursor MCP

```json
{
  "mcpServers": {
    "my-mcp-stdio": {
      "command": "npm",
      "args": [
        "start"
      ],
      "env": {
        "NODE_ENV": "development"
      }
    },
    "my-mcp-sse": {
      "url": "http://localhost:3001/sse"
    }
  }
}
```

## Возможности

- Создан с использованием FastMCP фреймворка для упрощённой реализации
- Поддержка двух транспортов: запуск MCP сервера через stdio или HTTP
- Полная поддержка TypeScript для безопасности типов
- Лёгкое добавление пользовательских инструментов, ресурсов и промптов
- Базовая настройка сервера с опциями транспорта stdio и HTTP
- Скрипты разработки и конфигурация включены
- Режим разработки с автоперезагрузкой

## Переменные окружения

### Опциональные
- `PORT` - порт HTTP сервера (по умолчанию 3001)
- `HOST` - адрес привязки хоста (по умолчанию 0.0.0.0)
- `NODE_ENV` - настройка окружения Node.js

## Ресурсы

- [GitHub Repository](https://github.com/mcpdotdirect/template-mcp-server)

## Примечания

Это шаблон/инструмент для создания MCP серверов, а не функциональный MCP сервер сам по себе. После создания используйте 'npm start' для stdio режима или 'npm run start:http' для HTTP режима. Скрипты по умолчанию используют Bun как среду выполнения, но могут быть изменены для использования Node.js. FastMCP предоставляет встроенные инструменты тестирования с командами 'npx fastmcp dev' и 'npx fastmcp inspect'.