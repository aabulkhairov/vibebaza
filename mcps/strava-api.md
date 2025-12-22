---
title: Strava API MCP сервер
description: Model Context Protocol (MCP) сервер, который предоставляет доступ к Strava API и позволяет языковым моделям запрашивать данные об активностях спортсменов из Strava.
tags:
- API
- Analytics
- Integration
- Productivity
author: Community
featured: false
install_command: strava&config=eyJjb21tYW5kIjoidXZ4IHN0cmF2YS1tY3Atc2VydmVyIiwiZW52Ijp7IlNUUkFWQV9DTElFTlRfSUQiOiJZT1VSX0NMSUVOVF9JRCIsIlNUUkFWQV9DTElFTlRfU0VDUkVUIjoiWU9VUl9DTElFTlRfU0VDUkVUIiwiU1RSQVZBX1JFRlJFU0hfVE9LRU4iOiJZT1VSX1JFRlJFU0hfVE9LRU4ifX0%3D
---

Model Context Protocol (MCP) сервер, который предоставляет доступ к Strava API и позволяет языковым моделям запрашивать данные об активностях спортсменов из Strava.

## Установка

### UVX

```bash
uvx strava-mcp-server
```

### Скрипт аутентификации

```bash
python get_strava_token.py
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "strava": {
            "command": "uvx",
            "args": [
                "strava-mcp-server"
            ],
            "env": {
                "STRAVA_CLIENT_ID": "YOUR_CLIENT_ID",
                "STRAVA_CLIENT_SECRET": "YOUR_CLIENT_SECRET",
                "STRAVA_REFRESH_TOKEN": "YOUR_REFRESH_TOKEN"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_activities` | Получить последние активности аутентифицированного спортсмена с опциональным параметром лимита (по умолчанию 10) |
| `get_activities_by_date_range` | Получить активности в определенном диапазоне дат с start_date, end_date и опциональным лимитом (по умолчанию... |
| `get_activity_by_id` | Получить подробную информацию о конкретной активности по activity_id |
| `get_recent_activities` | Получить активности за последние X дней с опциональными параметрами days (по умолчанию 7) и limit (по умолчанию 10) |

## Возможности

- Запрос последних активностей из Strava
- Получение активностей по диапазону дат в формате ISO
- Извлечение подробной информации об активности по ID
- Доступ к активностям за последние X дней
- Консистентный формат данных со стандартизированными единицами измерения (метры, секунды и т.д.)
- Комплексные данные об активности включая расстояние, скорость, высоту, калории и GPS координаты
- Человеко-читаемая обработка ошибок для распространенных проблем

## Переменные окружения

### Обязательные
- `STRAVA_CLIENT_ID` - Ваш Client ID для Strava API
- `STRAVA_CLIENT_SECRET` - Ваш Client Secret для Strava API
- `STRAVA_REFRESH_TOKEN` - Ваш Refresh Token для Strava API

## Примеры использования

```
What are my recent activities?
```

```
Show me my activities from last week
```

```
What was my longest run in the past month?
```

```
Get details about my latest cycling activity
```

## Ресурсы

- [GitHub Repository](https://github.com/tomekkorbak/strava-mcp-server)

## Примечания

Требует создания приложения Strava API и установки Authorization Callback Domain на 'localhost'. Включенный скрипт get_strava_token.py помогает с генерацией токена. Также поддерживает Claude Web через MCP расширение. Даты должны быть предоставлены в формате ISO (YYYY-MM-DD).