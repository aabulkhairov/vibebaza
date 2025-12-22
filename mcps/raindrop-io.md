---
title: Raindrop.io MCP сервер
description: Интеграция, которая позволяет LLM взаимодействовать с закладками Raindrop.io через Model Context Protocol (MCP), обеспечивая создание закладок, поиск и фильтрацию по тегам.
tags:
- Productivity
- API
- Integration
- Search
- Storage
author: hiromitsusasaki
featured: false
---

Интеграция, которая позволяет LLM взаимодействовать с закладками Raindrop.io через Model Context Protocol (MCP), обеспечивая создание закладок, поиск и фильтрацию по тегам.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @hiromitsusasaki/raindrop-io-mcp-server --client claude
```

### Из исходников

```bash
git clone https://github.com/hiromitsusasaki/raindrop-io-mcp-server
cd raindrop-io-mcp-server
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "raindrop": {
      "command": "node",
      "args": ["PATH_TO_BUILD/index.js"],
      "env": {
        "RAINDROP_TOKEN": "your_access_token_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `create-bookmark` | Создает новую закладку с опциональным заголовком, тегами и ID коллекции |
| `search-bookmarks` | Ищет закладки с опциональной фильтрацией по тегам |

## Возможности

- Создание закладок
- Поиск закладок
- Фильтрация по тегам

## Переменные окружения

### Обязательные
- `RAINDROP_TOKEN` - Ваш токен доступа к API Raindrop.io

## Ресурсы

- [GitHub Repository](https://github.com/hiromitsusasaki/raindrop-io-mcp-server)

## Примечания

Требует Node.js 16 или выше и аккаунт Raindrop.io с API токеном. Выпущен под лицензией MIT и открыт для контрибуций.