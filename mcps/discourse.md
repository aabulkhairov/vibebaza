---
title: Discourse MCP сервер
description: Node.js MCP сервер, который позволяет искать посты на форумах Discourse через Model Context Protocol.
tags:
- Search
- API
- Integration
- Messaging
author: AshDevFr
featured: false
---

Node.js MCP сервер, который позволяет искать посты на форумах Discourse через Model Context Protocol.

## Установка

### Docker

```bash
docker run -i --rm -e DISCOURSE_API_URL=https://try.discourse.org -e DISCOURSE_API_KEY=1234 -e DISCOURSE_API_USERNAME=ash ashdev/discourse-mcp-server
```

### NPX

```bash
npx -y @ashdev/discourse-mcp-server
```

### Docker Build

```bash
docker build -t ashdev/discourse-mcp-server .
```

## Конфигурация

### Claude Desktop - Docker

```json
{
  "mcpServers": {
    "discourse": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e", "DISCOURSE_API_URL=https://try.discourse.org",
        "-e", "DISCOURSE_API_KEY=1234",
        "-e", "DISCOURSE_API_USERNAME=ash",
        "ashdev/discourse-mcp-server"
      ]
    }
  }
}
```

### Claude Desktop - NPX

```json
{
  "mcpServers": {
    "discourse": {
      "command": "npx",
      "args": [
        "-y",
        "@ashdev/discourse-mcp-server"
      ],
      "env": {
        "DISCOURSE_API_URL": "https://try.discourse.org",
        "DISCOURSE_API_KEY": "1234",
        "DISCOURSE_API_USERNAME": "ash" 
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search_posts` | Поиск постов на форуме Discourse по строке запроса и возвращает массив объектов постов |

## Возможности

- Поиск постов на форуме Discourse через MCP протокол

## Переменные окружения

### Обязательные
- `DISCOURSE_API_URL` - URL форума Discourse (например, https://try.discourse.org)
- `DISCOURSE_API_KEY` - API ключ для аутентификации на форуме Discourse
- `DISCOURSE_API_USERNAME` - Имя пользователя для API аутентификации на форуме Discourse

## Ресурсы

- [GitHub Repository](https://github.com/AshDevFr/discourse-mcp-server)