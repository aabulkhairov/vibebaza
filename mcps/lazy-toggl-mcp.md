---
title: Lazy Toggl MCP сервер
description: Model Context Protocol (MCP) сервер, который предоставляет инструменты для взаимодействия с системой отслеживания времени Toggl, позволяя пользователям запускать/останавливать отслеживание времени, получать текущие записи и просматривать рабочие пространства.
tags:
- Productivity
- API
- Integration
author: Community
featured: false
---

Model Context Protocol (MCP) сервер, который предоставляет инструменты для взаимодействия с системой отслеживания времени Toggl, позволяя пользователям запускать/останавливать отслеживание времени, получать текущие записи и просматривать рабочие пространства.

## Установка

### Из исходного кода

```bash
cd lazy-toggl-mcp
uv sync
```

## Конфигурация

### Настройки MCP

```json
{
  "mcpServers": {
    "lazy-toggl-mcp": {
      "autoApprove": [],
      "disabled": false,
      "timeout": 60,
      "type": "stdio",
      "transportType": "stdio",
      "command": "uv",
      "args": [
        "run",
        "--directory",
        "/path/to/lazy-toggl-mcp",
        "python",
        "server.py"
      ],
      "env": {
        "TOGGL_API_TOKEN": "your-actual-api-token-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `start_tracking` | Начать отслеживание времени для новой задачи с опциональным рабочим пространством, проектом и тегами |
| `stop_tracking` | Остановить текущую запись времени |
| `list_workspaces` | Показать все доступные рабочие пространства с их ID и названиями |
| `show_current_time_entry` | Показать текущую запись времени с деталями: описание, рабочее пространство, продолжительность и теги |

## Возможности

- Запуск/остановка отслеживания времени
- Получение текущей записи
- Просмотр рабочих пространств
- Интеграция с Toggl Track API v9

## Переменные окружения

### Обязательные
- `TOGGL_API_TOKEN` - Ваш API токен Toggl для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/movstox/lazy-toggl-mcp)

## Примечания

Использует Toggl Track API v9. Требуется API токен из настроек профиля Toggl Track. Лицензия MIT.