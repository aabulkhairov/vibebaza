---
title: Zoom MCP сервер
description: Model Context Protocol (MCP) сервер для управления Zoom встречами через Claude или Cursor, позволяющий создавать, обновлять, удалять и получать информацию о Zoom встречах через стандартизированный MCP интерфейс.
tags:
- Productivity
- Integration
- API
- Messaging
author: Prathamesh0901
featured: false
---

Model Context Protocol (MCP) сервер для управления Zoom встречами через Claude или Cursor, позволяющий создавать, обновлять, удалять и получать информацию о Zoom встречах через стандартизированный MCP интерфейс.

## Установка

### NPX

```bash
npx -y @prathamesh0901/zoom-mcp-server
```

### Из исходников

```bash
git clone https://github.com/Prathamesh0901/zoom-mcp-server.git
cd zoom-mcp-server
npm install
```

## Конфигурация

### Claude Desktop / Cursor

```json
{
  "mcpServers": {
    "zoom": {
      "command": "npx",
      "args": [
        "-y", "@prathamesh0901/zoom-mcp-server"
      ],
      "env": {
        "ZOOM_ACCOUNT_ID": "Your Zoom Account ID",
        "ZOOM_CLIENT_ID": "Your Zoom Client ID",
        "ZOOM_CLIENT_SECRET": "Your Zoom Client Secret"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_meetings` | Получить все активные Zoom встречи |
| `create_meeting` | Создать новую Zoom встречу |
| `update_meeting` | Обновить существующую встречу |
| `delete_meeting` | Удалить Zoom встречу |

## Возможности

- Создание новых Zoom встреч
- Обновление существующих Zoom встреч
- Удаление Zoom встреч
- Получение всех активных Zoom встреч
- Валидация параметров с помощью Zod схем
- Интеграция с Server-to-Server OAuth приложением

## Переменные окружения

### Обязательные
- `ZOOM_ACCOUNT_ID` - Ваш Zoom Account ID из учетных данных приложения
- `ZOOM_CLIENT_ID` - Ваш Zoom Client ID из учетных данных приложения
- `ZOOM_CLIENT_SECRET` - Ваш Zoom Client Secret из учетных данных приложения

## Ресурсы

- [GitHub Repository](https://github.com/Prathamesh0901/zoom-mcp-server)

## Примечания

Требует создания Server-to-Server OAuth приложения в Zoom Marketplace со всеми разрешениями для встреч. Сервер использует валидацию параметров через Zod схемы и интегрируется с AI инструментами типа Claude и Cursor.