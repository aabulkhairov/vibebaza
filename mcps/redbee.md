---
title: Redbee MCP сервер
description: MCP сервер для Red Bee Media OTT платформы, который предоставляет 33 инструмента для аутентификации, поиска контента, управления пользователями, покупок и системных операций со стриминговыми сервисами.
tags:
- Media
- API
- Search
- Integration
- Analytics
author: Tamsi
featured: false
---

MCP сервер для Red Bee Media OTT платформы, который предоставляет 33 инструмента для аутентификации, поиска контента, управления пользователями, покупок и системных операций со стриминговыми сервисами.

## Установка

### uvx (Рекомендуется)

```bash
# Test the server
uvx redbee-mcp --help

# Stdio mode (original)
uvx redbee-mcp --stdio --customer YOUR_CUSTOMER --business-unit YOUR_BU

# HTTP mode (new)
uvx redbee-mcp --http --customer YOUR_CUSTOMER --business-unit YOUR_BU

# Both modes simultaneously
uvx redbee-mcp --both --customer YOUR_CUSTOMER --business-unit YOUR_BU
```

### pip

```bash
pip install redbee-mcp

# Same usage as uvx, but with redbee-mcp command
redbee-mcp --http --customer YOUR_CUSTOMER --business-unit YOUR_BU
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "redbee-mcp": {
      "command": "uvx",
      "args": ["redbee-mcp", "--stdio"],
      "env": {
        "REDBEE_CUSTOMER": "CUSTOMER_NAME",
        "REDBEE_BUSINESS_UNIT": "BUSINESS_UNIT_NAME"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `login_user` | Аутентификация с помощью имени пользователя и пароля |
| `create_anonymous_session` | Создание анонимной сессии |
| `validate_session_token` | Валидация существующей сессии |
| `logout_user` | Выход из системы и аннулирование сессии |
| `get_public_asset_details` | Получение деталей ассета через публичную конечную точку (без авторизации) |
| `search_content_v2` | Поиск V2: произвольный текстовый запрос по полям ассетов (включая описания) |
| `get_asset_details` | Получение детальной информации об ассете |
| `get_playback_info` | Получение URL-адресов стрима и информации о воспроизведении |
| `search_assets_autocomplete` | Предложения для автозаполнения поиска |
| `get_epg_for_channel` | Получение электронной программы передач для канала |
| `get_episodes_for_season` | Получение всех эпизодов в сезоне |
| `get_assets_by_tag` | Получение ассетов по типу тега (например, происхождение) |
| `list_assets` | Список ассетов с расширенными фильтрами |
| `search_multi_v3` | Мультипоиск по ассетам, тегам и участникам |
| `get_asset_collection_entries` | Получение записей коллекции для коллекции ассетов |

## Возможности

- Множественные режимы работы: Stdio, HTTP, SSE и одновременные режимы
- 33 инструмента для комплексной интеграции с платформой Red Bee Media
- Аутентификация и управление сессиями
- Поиск контента с расширенной фильтрацией и автозаполнением
- Управление профилем пользователя и настройками
- Обработка покупок и транзакций
- Доступ к электронной программе передач (EPG)
- Поддержка Server-Sent Events в реальном времени
- REST API с JSON-RPC для веб-интеграции
- Управление сезонами и эпизодами ТВ-шоу

## Переменные окружения

### Обязательные
- `REDBEE_CUSTOMER` - Идентификатор клиента Red Bee
- `REDBEE_BUSINESS_UNIT` - Бизнес-единица Red Bee

### Опциональные
- `REDBEE_EXPOSURE_BASE_URL` - Базовый URL API
- `REDBEE_USERNAME` - Имя пользователя для аутентификации
- `REDBEE_PASSWORD` - Пароль для аутентификации
- `REDBEE_SESSION_TOKEN` - Существующий токен сессии
- `REDBEE_DEVICE_ID` - Идентификатор устройства
- `REDBEE_CONFIG_ID` - ID конфигурации
- `REDBEE_TIMEOUT` - Таймаут запроса в секундах

## Примеры использования

```
Search for French documentaries about nature
```

```
Find French movies
```

```
Get TV show information for Game of Thrones
```

```
Search for comedy movies
```

```
Get episodes for a TV season
```

## Ресурсы

- [GitHub Repository](https://github.com/Tamsi/redbee-mcp)

## Примечания

Версия 1.4.0+ поддерживает HTTP/SSE режим для веб-интеграции наряду с традиционным stdio режимом. Сервер обеспечивает комплексную интеграцию с Red Bee Media OTT платформой с поддержкой как AI агентов, так и веб-приложений. Включает примеры продакшн деплоя с Docker и конфигурациями systemd сервисов.