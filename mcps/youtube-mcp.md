---
title: YouTube MCP сервер
description: MCP сервер для интеграции с YouTube API, который позволяет искать видео, создавать и управлять плейлистами, а также взаимодействовать с YouTube напрямую через Claude Desktop или другие MCP клиенты.
tags:
- Media
- API
- Integration
- Productivity
author: aardeshir
featured: false
---

MCP сервер для интеграции с YouTube API, который позволяет искать видео, создавать и управлять плейлистами, а также взаимодействовать с YouTube напрямую через Claude Desktop или другие MCP клиенты.

## Установка

### Глобальная установка через NPM

```bash
npm install -g @a.ardeshir/youtube-mcp
```

### Из GitHub

```bash
git clone https://github.com/aardeshir/youtube-mcp.git
cd youtube-mcp
npm install
```

## Конфигурация

### Claude Desktop (установка через NPM)

```json
{
  "mcpServers": {
    "youtube-mcp": {
      "command": "npx",
      "args": ["-y", "@a.ardeshir/youtube-mcp"],
      "env": {
        "YOUTUBE_API_KEY": "your-api-key",
        "YOUTUBE_CLIENT_ID": "your-client-id",
        "YOUTUBE_CLIENT_SECRET": "your-client-secret",
        "YOUTUBE_REFRESH_TOKEN": "your-refresh-token"
      }
    }
  }
}
```

### Claude Desktop (установка через GitHub)

```json
{
  "mcpServers": {
    "youtube-mcp": {
      "command": "node",
      "args": ["/path/to/youtube-mcp/index.js"],
      "env": {
        "YOUTUBE_API_KEY": "your-api-key",
        "YOUTUBE_CLIENT_ID": "your-client-id",
        "YOUTUBE_CLIENT_SECRET": "your-client-secret",
        "YOUTUBE_REFRESH_TOKEN": "your-refresh-token"
      }
    }
  }
}
```

## Возможности

- Поиск видео на YouTube
- Создание и управление плейлистами
- Добавление видео в плейлисты
- Просмотр пользовательских плейлистов
- Удаление плейлистов

## Переменные окружения

### Обязательные
- `YOUTUBE_API_KEY` - ключ YouTube Data API v3 для доступа только на чтение
- `YOUTUBE_CLIENT_ID` - OAuth 2.0 client ID из Google Cloud Console
- `YOUTUBE_CLIENT_SECRET` - OAuth 2.0 client secret из Google Cloud Console
- `YOUTUBE_REFRESH_TOKEN` - OAuth 2.0 refresh токен для доступа к YouTube данным пользователя

## Примеры использования

```
Search YouTube for "piano tutorials"
```

```
Create a YouTube playlist called "My Favorites"
```

```
Show my YouTube playlists
```

## Ресурсы

- [GitHub Repository](https://github.com/aardeshir/youtube-mcp)

## Примечания

Требует Node.js 18+, доступ к YouTube Data API v3 и аккаунт Google Cloud Console. Включает мастер настройки OAuth (команда youtube-mcp-setup) для автоматической генерации учетных данных. Имеет ежедневные лимиты API, которые могут потребовать увеличения при интенсивном использовании.