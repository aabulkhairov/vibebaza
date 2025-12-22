---
title: Adobe Commerce MCP сервер
description: MCP сервер для работы с Adobe Commerce GraphQL API. Предоставляет инструменты
  для доступа к интроспекции схемы и помощи в написании GraphQL операций.
tags:
- API
- Integration
- Code
author: rafaelstz
featured: false
---

MCP сервер для работы с Adobe Commerce GraphQL API. Предоставляет инструменты для доступа к интроспекции схемы и помощи в написании GraphQL операций.

## Установка

### NPX

```bash
npx -y @rafaelcg/adobe-commerce-dev-mcp@latest
```

### Из исходников

```bash
npm install
npm run build
node <absolute_path_of_project>/dist/index.js
```

## Конфигурация

### MCP Client (Linux/Mac)

```json
{
  "mcpServers": {
    "adobe-commerce-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@rafaelcg/adobe-commerce-dev-mcp@latest"]
    }
  }
}
```

### MCP Client (Windows)

```json
{
  "mcpServers": {
    "adobe-commerce-dev-mcp": {
      "command": "cmd",
      "args": ["/k", "npx", "-y", "@rafaelcg/adobe-commerce-dev-mcp@latest"]
    }
  }
}
```

### Локальная разработка

```json
{
  "mcpServers": {
    "adobe-commerce-dev-mcp": {
      "command": "node",
      "args": [
        "/Users/rafael/Herd/shopify-dev-mcp/dist/index.js"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `introspect_admin_schema` | Доступ и поиск по GraphQL схеме Adobe Commerce |

## Возможности

- GraphQL интроспекция схемы для Adobe Commerce
- Помощь в написании GraphQL операций
- Прямое использование NPM пакета без локальной установки
- Кроссплатформенная поддержка (Windows, Linux, Mac)

## Примеры использования

```
Help you write GraphQL operations for the Adobe Commerce API
```

## Ресурсы

- [GitHub Repository](https://github.com/rafaelstz/adobe-commerce-dev-mcp)

## Примечания

Построен с использованием MCP SDK. При использовании npx всегда используется последняя версия из NPM. Лицензия: ISC.
