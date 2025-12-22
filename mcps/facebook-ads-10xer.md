---
title: Facebook Ads 10xeR MCP сервер
description: MCP сервер, который предоставляет функциональность Facebook Ads, позволяя получать доступ к рекламным данным, аналитике, производительности креативов и информации об аккаунтах через естественные языковые диалоги.
tags:
- Analytics
- API
- Finance
- Media
- Integration
author: Community
featured: false
---

MCP сервер, который предоставляет функциональность Facebook Ads, позволяя получать доступ к рекламным данным, аналитике, производительности креативов и информации об аккаунтах через естественные языковые диалоги.

## Установка

### NPM Global

```bash
npm install -g facebook-ads-mcp-server
```

### Из исходников

```bash
cd facebook-ads-mcp
npm install
```

## Конфигурация

### Claude Desktop (OAuth)

```json
{
  "mcpServers": {
    "facebook-ads": {
      "command": "facebook-ads-mcp",
      "env": {
        "FACEBOOK_APP_ID": "your_facebook_app_id",
        "FACEBOOK_APP_SECRET": "your_facebook_app_secret",
        "FACEBOOK_REDIRECT_URI": "http://localhost:3002/auth/callback"
      }
    }
  }
}
```

### Claude Desktop (Token)

```json
{
  "mcpServers": {
    "facebook-ads": {
      "command": "facebook-ads-mcp",
      "env": {
        "FACEBOOK_ACCESS_TOKEN": "EAAxxxxxxxxxxxxx",
        "FACEBOOK_API_VERSION": "v23.0"
      }
    }
  }
}
```

### MCP интеграция

```json
{
  "mcpServers": {
    "facebook-ads-mcp": {
      "command": "node",
      "args": ["src/index.js"],
      "cwd": "/path/to/facebook-ads-mcp",
      "env": {
        "FACEBOOK_ACCESS_TOKEN": "your_facebook_access_token"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `facebook_list_ad_accounts` | Показывает все рекламные аккаунты Facebook, доступные с предоставленными учетными данными |
| `facebook_fetch_pagination_url` | Получает данные из URL пагинации Facebook Graph API |
| `facebook_get_details_of_ad_account` | Получает детали конкретного рекламного аккаунта на основе запрошенных полей |
| `facebook_get_adaccount_insights` | Получает аналитику производительности для указанного рекламного аккаунта Facebook с расширенным отслеживанием конверсий |
| `facebook_get_activities_by_adaccount` | Получает активности для рекламного аккаунта Facebook |
| `facebook_get_ad_creatives` | Получает рекламные креативы с миниатюрами и анализом производительности |

## Возможности

- OAuth авторизация: Безопасная аутентификация Facebook через браузер
- Управление токенами: Автоматическое безопасное сохранение и получение токенов
- Управление сессиями: Вход, выход и проверка статуса аутентификации
- Список рекламных аккаунтов: Получение всех доступных рекламных аккаунтов Facebook
- Детали аккаунта: Получение подробной информации о конкретных рекламных аккаунтах
- Аналитика аккаунта: Получение метрик производительности и данных аналитики
- Активности аккаунта: Получение логов активности для рекламных аккаунтов
- Поддержка пагинации: Обработка больших наборов данных с автоматической пагинацией
- Аналитика креативов и миниатюры: Миниатюры рекламных креативов с анализом производительности
- Расширенное отслеживание конверсий: Автоматически включает поле конверсий для лучшего качества данных

## Переменные окружения

### Обязательные
- `FACEBOOK_ACCESS_TOKEN` - токен доступа Facebook для аутентификации API

### Опциональные
- `FACEBOOK_APP_ID` - ID приложения Facebook для OAuth аутентификации
- `FACEBOOK_APP_SECRET` - секретный ключ приложения Facebook для OAuth аутентификации
- `FACEBOOK_REDIRECT_URI` - URI перенаправления OAuth для колбэка аутентификации
- `FACEBOOK_API_VERSION` - версия Facebook API для использования
- `FACEBOOK_BASE_URL` - базовый URL Facebook Graph API
- `MCP_SERVER_NAME` - идентификатор имени MCP сервера
- `DEBUG` - включить отладочное логирование
- `LOG_LEVEL` - уровень логирования (info, debug, error)

## Примеры использования

```
Войти в Facebook
```

```
Проверить мой статус аутентификации Facebook
```

```
Показать все мои рекламные аккаунты Facebook
```

```
Какой текущий баланс и статус моего основного рекламного аккаунта?
```

```
Получить аналитику производительности для моего рекламного аккаунта за последние 30 дней
```

## Ресурсы

- [GitHub Repository](https://github.com/fortytwode/10xer)

## Примечания

Требует настройки приложения Facebook Developer с конфигурацией OAuth. токен доступа должен иметь разрешения: ads_read, ads_management, business_management. Включает расширенное отслеживание конверсий, которое автоматически добавляет поле конверсий для лучшего качества данных. Версия v1.2.0 включает новую аналитику креативов с миниатюрами и анализом производительности.