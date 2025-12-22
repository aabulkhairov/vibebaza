---
title: Calendly-mcp-server MCP сервер
description: MCP сервер для интеграции с Calendly API, предоставляющий инструменты для управления событиями, приглашенными, планированием и пользовательской информацией с поддержкой нового Scheduling API.
tags:
- Productivity
- API
- Integration
- CRM
author: meAmitPatil
featured: false
---

MCP сервер для интеграции с Calendly API, предоставляющий инструменты для управления событиями, приглашенными, планированием и пользовательской информацией с поддержкой нового Scheduling API.

## Установка

### NPX

```bash
npx calendly-mcp-server
```

### Ручная установка

```bash
git clone https://github.com/meAmitPatil/calendly-mcp-server.git
cd calendly-mcp-server
npm install
npm run build
```

## Конфигурация

### Claude Desktop (NPX с Personal Access Token)

```json
{
  "mcpServers": {
    "calendly": {
      "command": "npx",
      "args": ["calendly-mcp-server"],
      "env": {
        "CALENDLY_API_KEY": "your_personal_access_token_here",
        "CALENDLY_USER_URI": "https://api.calendly.com/users/your_user_id",
        "CALENDLY_ORGANIZATION_URI": "https://api.calendly.com/organizations/your_org_id"
      }
    }
  }
}
```

### Claude Desktop (NPX с OAuth 2.0)

```json
{
  "mcpServers": {
    "calendly": {
      "command": "npx",
      "args": ["calendly-mcp-server"],
      "env": {
        "CALENDLY_CLIENT_ID": "your_client_id_here",
        "CALENDLY_CLIENT_SECRET": "your_client_secret_here",
        "CALENDLY_ACCESS_TOKEN": "your_access_token_here",
        "CALENDLY_REFRESH_TOKEN": "your_refresh_token_here",
        "CALENDLY_USER_URI": "https://api.calendly.com/users/your_user_id",
        "CALENDLY_ORGANIZATION_URI": "https://api.calendly.com/organizations/your_org_id"
      }
    }
  }
}
```

### Claude Desktop (локальная установка)

```json
{
  "mcpServers": {
    "calendly": {
      "command": "node",
      "args": ["path/to/calendly-mcp-server/dist/index.js"],
      "env": {
        "CALENDLY_API_KEY": "your_personal_access_token_here",
        "CALENDLY_USER_URI": "https://api.calendly.com/users/your_user_id",
        "CALENDLY_ORGANIZATION_URI": "https://api.calendly.com/organizations/your_org_id"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_oauth_url` | Генерация OAuth URL авторизации для аутентификации пользователя |
| `exchange_code_for_tokens` | Обмен кода авторизации на токены доступа и обновления |
| `refresh_access_token` | Обновление токена доступа с помощью токена обновления |
| `get_current_user` | Получение информации о текущем аутентифицированном пользователе |
| `list_events` | Список запланированных событий с опциональной фильтрацией |
| `get_event` | Получение деталей конкретного события |
| `list_event_invitees` | Список приглашенных для конкретного события |
| `cancel_event` | Отмена конкретного события |
| `list_organization_memberships` | Список членств в организации для аутентифицированного пользователя |
| `list_event_types` | Список доступных типов событий для планирования встреч |
| `get_event_type_availability` | Получение доступных временных слотов для конкретного типа события |
| `schedule_event` | Планирование встречи путем создания приглашенного для конкретного типа события и времени |

## Возможности

- Информация о пользователе: получение деталей текущего аутентифицированного пользователя
- Управление событиями: просмотр, получение и отмена запланированных событий
- Управление приглашенными: просмотр и управление приглашенными на события
- Организация: просмотр членств в организации
- Прямое планирование встреч: программное бронирование встреч без редиректов
- Обнаружение типов событий: просмотр доступных типов событий для планирования
- Доступность в реальном времени: проверка доступных временных слотов для любого типа события
- Полный процесс бронирования: сквозное планирование с синхронизацией календаря и уведомлениями
- Поддержка локаций: Zoom, Google Meet, Teams, физические локации и пользовательские варианты

## Переменные окружения

### Опциональные
- `CALENDLY_API_KEY` - Personal Access Token для аутентификации
- `CALENDLY_CLIENT_ID` - OAuth client ID для публичных приложений
- `CALENDLY_CLIENT_SECRET` - OAuth client secret для публичных приложений
- `CALENDLY_ACCESS_TOKEN` - OAuth токен доступа
- `CALENDLY_REFRESH_TOKEN` - OAuth токен обновления
- `CALENDLY_USER_URI` - Пользовательский URI для лучшей производительности и автоматических настроек по умолчанию
- `CALENDLY_ORGANIZATION_URI` - Организационный URI для лучшей производительности и автоматических настроек по умолчанию

## Примеры использования

```
Show me my Calendly events
```

```
Show me my event types
```

```
Check availability for my 30-minute consultation next week
```

```
Schedule a meeting with john@company.com for tomorrow at 2 PM
```

```
Book a client onboarding call for Friday
```

## Ресурсы

- [GitHub Repository](https://github.com/meAmitPatil/calendly-mcp-server)

## Примечания

Поддерживает аутентификацию как через Personal Access Token, так и через OAuth 2.0. Scheduling API требует платный план Calendly (Standard или выше). Включает в себя комплексный раздел устранения неполадок для распространенных проблем с NPX, аутентификацией и API.