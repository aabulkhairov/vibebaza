---
title: Oura MCP сервер
description: Сервер Model Context Protocol (MCP), который предоставляет доступ к Oura API, позволяя языковым моделям запрашивать данные о сне, готовности и устойчивости с устройств Oura.
tags:
- API
- Analytics
- Monitoring
- Integration
author: tomekkorbak
featured: false
---

Сервер Model Context Protocol (MCP), который предоставляет доступ к Oura API, позволяя языковым моделям запрашивать данные о сне, готовности и устойчивости с устройств Oura.

## Установка

### UVX

```bash
uvx oura-mcp-server
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "oura": {
            "command": "uvx",
            "args": [
                "oura-mcp-server"
            ],
            "env": {
                "OURA_API_TOKEN": "YOUR_OURA_API_TOKEN"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_sleep_data` | Получить данные о сне за определенный период (start_date: str, end_date: str) |
| `get_readiness_data` | Получить данные о готовности за определенный период (start_date: str, end_date: str) |
| `get_resilience_data` | Получить данные об устойчивости за определенный период (start_date: str, end_date: str) |
| `get_today_sleep_data` | Получить данные о сне за сегодня |
| `get_today_readiness_data` | Получить данные о готовности за сегодня |
| `get_today_resilience_data` | Получить данные об устойчивости за сегодня |

## Возможности

- Запрос данных о сне, готовности и устойчивости из Oura API
- Поддержка запросов как за период дат, так и за сегодня
- Даты в ISO формате (YYYY-MM-DD)
- Понятные сообщения об ошибках для частых проблем
- Обработка ошибок аутентификации API
- Обработка проблем с сетевым подключением

## Переменные окружения

### Обязательные
- `OURA_API_TOKEN` - Персональный токен доступа из Oura Developer Portal для аутентификации в API

## Примеры использования

```
Какой у меня балл сна сегодня?
```

```
Покажи мои данные о готовности за прошлую неделю
```

```
Как был мой сон с 1 по 7 января?
```

```
Какой у меня балл устойчивости сегодня?
```

## Ресурсы

- [GitHub Repository](https://github.com/tomekkorbak/oura-mcp-server)

## Примечания

Требует токен Oura API, который можно получить в Oura Developer Portal (https://cloud.ouraring.com/v2/docs). Доступен в PyPI как 'oura-mcp-server'. Лицензирован под MIT License.