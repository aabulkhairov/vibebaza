---
title: Bilibili MCP сервер
description: MCP сервер, который предоставляет инструменты для получения профилей пользователей Bilibili, метаданных видео и поиска видео с помощью API bilibili.com.
tags:
- API
- Media
- Search
- Web Scraping
author: wangshunnn
featured: false
---

MCP сервер, который предоставляет инструменты для получения профилей пользователей Bilibili, метаданных видео и поиска видео с помощью API bilibili.com.

## Установка

### NPX

```bash
npx -y @wangshunnn/bilibili-mcp-server
```

### Из исходного кода

```bash
pnpm i
pnpm build
```

## Конфигурация

### Claude Desktop (NPM)

```json
{
  "mcpServers": {
    "bilibili": {
      "command": "npx",
      "args": ["-y", "@wangshunnn/bilibili-mcp-server"]
    }
  }
}
```

### Claude Desktop (локально)

```json
{
  "mcpServers": {
    "bilibili": {
      "command": "node",
      "args": [
        "/ABSOLUTE/PATH/TO/PARENT/FOLDER/bilibili-mcp-server/dist/index.js"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_user_info` | Получить информацию о пользователе по mid (ID пользователя) |
| `search_video_info` | Найти информацию о видео по bvid (ID видео) |
| `search_videos` | Поиск видео по ключевым словам |

## Возможности

- Получение информации о пользователе по mid
- Поиск информации о видео по bvid
- Поиск видео по ключевым словам

## Ресурсы

- [GitHub Repository](https://github.com/wangshunnn/bilibili-mcp-server)

## Примечания

Создан с использованием документации bilibili-API-collect. Поддерживает как установку через NPM, так и локальную разработку. Включает демо-видео и скриншоты для интеграции с Claude Desktop.