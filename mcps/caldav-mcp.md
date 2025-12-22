---
title: CalDAV MCP сервер
description: CalDAV сервер для Model Context Protocol (MCP), который предоставляет операции с календарём в виде инструментов для AI ассистентов, позволяя подключаться к CalDAV серверам для создания и просмотра календарных событий.
tags:
- Productivity
- API
- Integration
author: dominik1001
featured: false
---

CalDAV сервер для Model Context Protocol (MCP), который предоставляет операции с календарём в виде инструментов для AI ассистентов, позволяя подключаться к CalDAV серверам для создания и просмотра календарных событий.

## Установка

### NPX

```bash
npx caldav-mcp
```

### Из исходного кода

```bash
npx tsc
node index.js
```

## Конфигурация

### Конфигурация MCP сервера

```json
{
  "mcpServers": {
    ...,
    "calendar": {
      "command": "npx",
      "args": [
        "caldav-mcp"
      ],
      "env": {
        "CALDAV_BASE_URL": "<CalDAV server URL>",
        "CALDAV_USERNAME": "<CalDAV username>",
        "CALDAV_PASSWORD": "<CalDAV password>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create-event` | Создаёт новое календарное событие с параметрами названия, времени начала и окончания |
| `list-events` | Выводит список событий в указанном временном диапазоне, используя параметры начальной и конечной даты |

## Возможности

- Подключение к CalDAV серверам
- Создание календарных событий
- Просмотр календарных событий в определённом временном диапазоне

## Переменные окружения

### Обязательные
- `CALDAV_BASE_URL` - URL CalDAV сервера
- `CALDAV_USERNAME` - Имя пользователя CalDAV
- `CALDAV_PASSWORD` - Пароль CalDAV

## Ресурсы

- [GitHub Repository](https://github.com/dominik1001/caldav-mcp)

## Примечания

Требует компиляции TypeScript перед запуском. Лицензия MIT.