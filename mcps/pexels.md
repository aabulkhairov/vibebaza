---
title: Pexels MCP сервер
description: Model Context Protocol сервер, который предоставляет доступ к Pexels API
  для поиска и получения фотографий, видео и коллекций.
tags:
- API
- Media
- Search
author: Community
featured: false
---

Model Context Protocol сервер, который предоставляет доступ к Pexels API для поиска и получения фотографий, видео и коллекций.

## Установка

### uv (рекомендуется)

```bash
uvx pexels-mcp-server
```

### pip для проекта

```bash
pip install -r requirements.txt
```

### pip глобально

```bash
pip install pexels-mcp-server
```

## Конфигурация

### Claude Desktop (uv)

```json
{
    "mcpServers": {
        "pexels": {
            "command": "uvx",
            "args": ["pexels-mcp-server"],
            "env": {
                "PEXELS_API_KEY": "<Your Pexels API key>"
            }
        }
    }
}
```

### Claude Desktop (pip проект)

```json
{
    "mcpServers": {
        "pexels": {
            "command": "python3",
            "args": ["-m", "pexels_mcp_server"],
            "env": {
                "PEXELS_API_KEY": "<Your Pexels API key>"
            }
        }
    }
}
```

### Claude Desktop (pip глобально)

```json
{
    "mcpServers": {
        "pexels": {
            "command": "python3",
            "args": ["pexels-mcp-server"],
            "env": {
                "PEXELS_API_KEY": "<Your Pexels API key>"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `photos_search` | Поиск фотографий |
| `photos_curated` | Список кураторских фотографий |
| `photo_get` | Получить фотографию по id |
| `videos_search` | Поиск видео |
| `videos_popular` | Список популярных видео |
| `video_get` | Получить видео по id |
| `collections_featured` | Список рекомендуемых коллекций |
| `collections_media` | Список медиа в коллекции |

## Возможности

- Поиск фотографий через Pexels API
- Получение кураторских фотографий
- Получение конкретных фотографий по ID
- Поиск видео
- Список популярных видео
- Получение конкретных видео по ID
- Доступ к рекомендуемым коллекциям
- Список медиа в коллекциях

## Переменные окружения

### Обязательные
- `PEXELS_API_KEY` - Ваш Pexels API ключ для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/garylab/pexels-mcp-server)

## Примечания

Сервер можно отладить с помощью MCP инспектора командой 'npx @modelcontextprotocol/inspector uvx pexels-mcp-server'. Лицензирован под MIT License.