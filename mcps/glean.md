---
title: Glean MCP сервер
description: Реализация MCP сервера, которая интегрируется с Glean API, предоставляя функциональность поиска и возможности Q&A чатбота.
tags:
- Search
- AI
- API
- Integration
author: longyi1207
featured: false
---

Реализация MCP сервера, которая интегрируется с Glean API, предоставляя функциональность поиска и возможности Q&A чатбота.

## Установка

### Docker

```bash
docker build -t glean-server:latest -f src/glean/Dockerfile .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "glean-server": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "GLEAN_API_KEY",
        "-e",
        "GLEAN_DOMAIN",
        "glean-server"
      ],
      "env": {
        "GLEAN_API_KEY": "YOUR_API_KEY_HERE",
        "GLEAN_DOMAIN": "YOUR_DOMAIN_HERE"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `Search` | Список результатов поиска по заданному запросу |
| `Chat` | Q&A с чатботом |

## Возможности

- Функциональность поиска через Glean API
- Возможности Q&A чатбота
- Деплой на основе Docker

## Переменные окружения

### Обязательные
- `GLEAN_API_KEY` - API ключ для доступа к сервисам Glean
- `GLEAN_DOMAIN` - Домен для доступа к Glean API

## Ресурсы

- [GitHub Repository](https://github.com/longyi1207/glean-mcp-server)

## Примечания

Лицензирован под MIT License. Требует Docker для деплоя и учетные данные Glean API для функциональности.