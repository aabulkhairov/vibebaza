---
title: Drupal MCP сервер
description: TypeScript-based сервер протокола Model Context Protocol для Drupal, который предоставляет доступ к ресурсам, инструментам и промптам, определённым через Drupal API во время инициализации.
tags:
- API
- CRM
- Integration
- Web Scraping
- Code
author: Omedia
featured: false
---

TypeScript-based сервер протокола Model Context Protocol для Drupal, который предоставляет доступ к ресурсам, инструментам и промптам, определённым через Drupal API во время инициализации.

## Установка

### Из исходников

```bash
bun install
bun run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "mcp-server-drupal": {
      "command": "__BINARY_PATH__",
      "args": ["--drupalBaseUrl", "__DRUPAL_BASE_URL__"],
      "env": {}
    }
  }
}
```

## Возможности

- Все ресурсы, определённые Drupal API во время фазы инициализации
- Все инструменты, определённые Drupal API во время фазы инициализации
- Все промпты, определённые Drupal API во время фазы инициализации

## Ресурсы

- [GitHub Repository](https://github.com/Omedia/mcp-server-drupal)

## Примечания

Для разработки используйте 'bun run dev' для автоматической пересборки. Отладку можно выполнить с помощью MCP Inspector через 'bun run inspector'. Пути конфигурации: MacOS: ~/Library/Application Support/Claude/claude_desktop_config.json, Windows: %APPDATA%/Claude/claude_desktop_config.json