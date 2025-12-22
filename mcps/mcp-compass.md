---
title: MCP Compass MCP сервер
description: MCP Compass — это сервис для поиска и рекомендаций, который помогает исследовать серверы Model Context Protocol с помощью запросов на естественном языке, выступая в роли умного гида для поиска и понимания доступных MCP сервисов.
tags:
- Search
- AI
- Integration
- Analytics
- API
author: liuyoshio
featured: true
---

MCP Compass — это сервис для поиска и рекомендаций, который помогает исследовать серверы Model Context Protocol с помощью запросов на естественном языке, выступая в роли умного гида для поиска и понимания доступных MCP сервисов.

## Установка

### NPX

```bash
npx -y @liuyoshio/mcp-compass
```

### Из исходного кода

```bash
node /path/to/repo/build/index.js
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "mcp-compass": {
      "command": "npx",
      "args": [
        "-y",
        "@liuyoshio/mcp-compass"
      ]
    }
  }
}
```

### Claude Desktop (локально)

```json
{
  "mcpServers": {
    "mcp-compass": {
      "command": "node",
      "args": [
        "/path/to/repo/build/index.js"
      ]
    }
  }
}
```

## Возможности

- Умный поиск: находите MCP сервисы с помощью запросов на естественном языке
- Богатые метаданные: получайте подробную информацию о каждом сервисе
- Обновления в реальном времени: всегда актуальная информация о последних MCP сервисах
- Простая интеграция: легко интегрируется с любым AI-ассистентом, совместимым с MCP

## Ресурсы

- [GitHub Repository](https://github.com/liuyoshio/mcp-compass)

## Примечания

Вы можете попробовать поиск MCP напрямую на сайте https://mcphub.io/. Сервис помогает AI-ассистентам находить и понимать доступные MCP сервисы на основе запросов на естественном языке.