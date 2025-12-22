---
title: Apple Calendar MCP сервер
description: MCP сервер, который позволяет взаимодействовать с macOS Calendar на естественном языке для создания событий, их изменения, управления расписанием и поиска свободного времени.
tags:
- Productivity
- Integration
- API
author: Community
featured: false
---

MCP сервер, который позволяет взаимодействовать с macOS Calendar на естественном языке для создания событий, их изменения, управления расписанием и поиска свободного времени.

## Установка

### Из исходников

```bash
# Clone the repository
git clone https://github.com/Omar-V2/mcp-ical.git
cd mcp-ical

# Install dependencies
uv sync
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "mcp-ical": {
            "command": "uv",
            "args": [
                "--directory",
                "/ABSOLUTE/PATH/TO/PARENT/FOLDER/mcp-ical",
                "run",
                "mcp-ical"
            ]
        }
    }
}
```

## Возможности

- Создание событий на естественном языке с выбором календаря
- Поддержка местоположения и заметок для событий
- Умные напоминания и повторяющиеся события
- Интеллектуальное управление расписанием и проверка доступности
- Умные обновления и изменения событий
- Поддержка нескольких календарей, включая интеграцию с Google Calendar при синхронизации с iCloud
- Просмотр всех доступных календарей с умными предложениями

## Примеры использования

```
What's my schedule for next week?
```

```
Add a lunch meeting with Sarah tomorrow at noon
```

```
Schedule a team lunch next Thursday at 1 PM at Bistro Garden
```

```
Set up my weekly team sync every Monday at 9 AM with a 15-minute reminder
```

```
When am I free to schedule a 2-hour meeting next Tuesday?
```

## Ресурсы

- [GitHub Repository](https://github.com/Omar-v2/mcp-ical)

## Примечания

Требует macOS с настроенным приложением Calendar и пакетным менеджером uv. Claude должен быть запущен из терминала для корректного запроса разрешений календаря. При первом использовании команд календаря macOS запросит доступ к календарю. Тесты создают временные календари и должны запускаться только в среде разработки.