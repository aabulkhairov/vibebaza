---
title: mcp-meme-sticky MCP сервер
description: Создавайте AI-генерированные мемы с помощью MCP сервера, который может конвертировать созданные мемы в стикеры для Telegram или WhatsApp без необходимости использования API.
tags:
- AI
- Media
- Messaging
- Integration
- Productivity
author: nkapila6
featured: false
---

Создавайте AI-генерированные мемы с помощью MCP сервера, который может конвертировать созданные мемы в стикеры для Telegram или WhatsApp без необходимости использования API.

## Установка

### UVX

```bash
uvx --python=3.10 --from git+https://github.com/nkapila6/mcp-meme-sticky mcp-sticky
```

## Конфигурация

### Конфигурация MCP серверов

```json
{
  "mcpServers": {
    "mcp-sticky":{
      "command": "uvx",
        "args": [
          "--python=3.10",
          "--from",
          "git+https://github.com/nkapila6/mcp-meme-sticky",
          "mcp-sticky"
        ]
      }
  }
}
```

## Возможности

- Генерация пользовательских мемов на основе промптов
- Сохранение сгенерированных мемов на рабочий стол
- Конвертация мемов в стикеры для Telegram
- Создание Telegram ссылок для конвертации изображений в стикеры
- Автоматическое открытие Telegram вместо браузера
- Автоматическое открытие ссылок на изображения
- Использование готовых шаблонов memegen
- AI-управляемый выбор текста для мемов
- Не требует API

## Ресурсы

- [GitHub Repository](https://github.com/nkapila6/mcp-meme-sticky)

## Примечания

Использует Memegen, Mediapipe text embedder для выбора шаблонов, PythonAnywhere для хостинга Telegram бота, вдохновлен библиотекой icrawler и построен с FastMCP. Протестировано на Claude Desktop, Cursor и Goose. Конвертация стикеров для WhatsApp находится в разработке. Включает бейдж аудита безопасности от MseeP. Содержит дисклеймер об ответственности за AI-генерированный контент.