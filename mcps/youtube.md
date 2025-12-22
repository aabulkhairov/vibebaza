---
title: YouTube MCP сервер
description: Реализация сервера Model Context Protocol для YouTube, которая позволяет языковым моделям ИИ взаимодействовать с контентом YouTube через стандартизированный интерфейс для управления видео, обработки транскрипций, операций с каналами и работы с плейлистами.
tags:
- API
- Media
- Analytics
- Integration
- AI
author: ZubeidHendricks
featured: true
---

Реализация сервера Model Context Protocol для YouTube, которая позволяет языковым моделям ИИ взаимодействовать с контентом YouTube через стандартизированный интерфейс для управления видео, обработки транскрипций, операций с каналами и работы с плейлистами.

## Установка

### Глобальная установка через NPM

```bash
npm install -g zubeid-youtube-mcp-server
```

### NPX (без установки)

```bash
npx -y zubeid-youtube-mcp-server
```

### Smithery

```bash
npx -y @smithery/cli install @ZubeidHendricks/youtube --client claude
```

## Конфигурация

### Claude Desktop (глобальная установка)

```json
{
  "mcpServers": {
    "zubeid-youtube-mcp-server": {
      "command": "zubeid-youtube-mcp-server",
      "env": {
        "YOUTUBE_API_KEY": "your_youtube_api_key_here"
      }
    }
  }
}
```

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "youtube": {
      "command": "npx",
      "args": ["-y", "zubeid-youtube-mcp-server"],
      "env": {
        "YOUTUBE_API_KEY": "your_youtube_api_key_here"
      }
    }
  }
}
```

### Настройки пользователя VS Code

```json
{
  "mcp": {
    "inputs": [
      {
        "type": "promptString",
        "id": "apiKey",
        "description": "YouTube API Key",
        "password": true
      }
    ],
    "servers": {
      "youtube": {
        "command": "npx",
        "args": ["-y", "zubeid-youtube-mcp-server"],
        "env": {
          "YOUTUBE_API_KEY": "${input:apiKey}"
        }
      }
    }
  }
}
```

### Рабочая область VS Code

```json
{
  "inputs": [
    {
      "type": "promptString",
      "id": "apiKey",
      "description": "YouTube API Key",
      "password": true
    }
  ],
  "servers": {
    "youtube": {
      "command": "npx",
      "args": ["-y", "zubeid-youtube-mcp-server"],
      "env": {
        "YOUTUBE_API_KEY": "${input:apiKey}"
      }
    }
  }
}
```

## Возможности

- Получение деталей видео (название, описание, длительность и т.д.)
- Список видео канала
- Получение статистики видео (просмотры, лайки, комментарии)
- Поиск видео по YouTube
- Получение транскрипций видео
- Поддержка множества языков
- Получение субтитров с временными метками
- Поиск в транскрипциях
- Получение деталей канала
- Список плейлистов канала

## Переменные окружения

### Обязательные
- `YOUTUBE_API_KEY` - Ваш ключ YouTube Data API

### Опциональные
- `YOUTUBE_TRANSCRIPT_LANG` - Язык по умолчанию для транскрипций (по умолчанию 'en')

## Примеры использования

```
Получить детали для конкретного видео YouTube
```

```
Получить транскрипции с временными метками для видео
```

```
Искать видео по YouTube с определёнными терминами
```

```
Список всех видео с конкретного канала
```

```
Получить статистику и детали канала
```

## Ресурсы

- [GitHub Repository](https://github.com/ZubeidHendricks/youtube-mcp-server)

## Примечания

Требует настройки YouTube Data API v3 через Google Cloud Console. Создайте проект, включите YouTube Data API v3 и сгенерируйте API ключ для конфигурации.