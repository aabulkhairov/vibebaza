---
title: Google Analytics 4 MCP сервер
description: MCP сервер для Google Analytics 4, предоставляющий полную интеграцию с Google Analytics Data API для чтения отчетов и Measurement Protocol v2 для отправки событий.
tags:
- Analytics
- API
- Integration
- Monitoring
author: gomakers-ai
featured: false
---

MCP сервер для Google Analytics 4, предоставляющий полную интеграцию с Google Analytics Data API для чтения отчетов и Measurement Protocol v2 для отправки событий.

## Установка

### NPM Global

```bash
npm install -g mcp-google-analytics
```

### NPX

```bash
npx mcp-google-analytics
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "google-analytics": {
      "command": "npx",
      "args": ["-y", "mcp-google-analytics"],
      "env": {
        "GA_SERVICE_ACCOUNT_JSON": "/path/to/service-account.json",
        "GA_PROPERTY_ID": "123456789",
        "GA_MEASUREMENT_ID": "G-XXXXXXXXXX",
        "GA_API_SECRET": "your-api-secret"
      }
    }
  }
}
```

### Claude Desktop (Global)

```json
{
  "mcpServers": {
    "google-analytics": {
      "command": "mcp-google-analytics",
      "env": {
        "GA_SERVICE_ACCOUNT_JSON": "/path/to/service-account.json",
        "GA_PROPERTY_ID": "123456789",
        "GA_MEASUREMENT_ID": "G-XXXXXXXXXX",
        "GA_API_SECRET": "your-api-secret"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "google-analytics": {
      "command": "npx",
      "args": ["-y", "mcp-google-analytics"],
      "env": {
        "GA_SERVICE_ACCOUNT_JSON": "/path/to/service-account.json",
        "GA_PROPERTY_ID": "123456789",
        "GA_MEASUREMENT_ID": "G-XXXXXXXXXX",
        "GA_API_SECRET": "your-api-secret"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `ga_run_report` | Выполнение кастомных отчетов с измерениями и метриками |
| `ga_run_realtime_report` | Получение данных в реальном времени (последние 30 минут) |
| `ga_get_metadata` | Получение всех доступных измерений и метрик для вашего ресурса |
| `ga_list_accounts` | Список всех GA аккаунтов, доступных сервисному аккаунту |
| `ga_list_properties` | Список GA4 ресурсов, опционально отфильтрованных по ID аккаунта |
| `ga_get_property` | Получение деталей о настроенном ресурсе |
| `ga_list_data_streams` | Список потоков данных для настроенного ресурса |
| `ga_run_pivot_report` | Выполнение сводных отчетов с измерениями строк/столбцов |
| `ga_run_funnel_report` | Выполнение воронкового анализа для отслеживания прогресса пользователей |
| `ga_batch_run_reports` | Выполнение нескольких отчетов в одном запросе |
| `ga_send_event` | Отправка кастомных событий в GA4 |
| `ga_validate_event` | Валидация событий перед отправкой (использует debug endpoint) |
| `ga_send_pageview` | Отправка событий просмотра страниц |
| `ga_send_purchase` | Отправка событий покупок в ecommerce |
| `ga_send_login` | Отправка событий авторизации |

## Возможности

- Интеграция с Google Analytics Data API для чтения отчетов
- Интеграция с Measurement Protocol v2 для отправки событий
- Оптимизация токенов с лимитом в 10 результатов по умолчанию
- Отчеты по данным в реальном времени (последние 30 минут)
- Поддержка кастомных измерений и метрик
- Сводные таблицы и отчеты воронкового анализа
- Пакетная обработка отчетов
- Валидация событий перед отправкой
- Возможности отслеживания ecommerce
- Поддержка debug логирования

## Переменные окружения

### Обязательные
- `GA_SERVICE_ACCOUNT_JSON` - Путь к JSON файлу сервисного аккаунта или содержимое JSON напрямую для доступа к Data API
- `GA_PROPERTY_ID` - Числовой ID GA4 ресурса для чтения данных
- `GA_MEASUREMENT_ID` - GA4 Measurement ID (формат: G-XXXXXXXXXX) для отправки событий
- `GA_API_SECRET` - API секрет для Measurement Protocol

### Опциональные
- `DEBUG` - Включение debug логирования (установите в mcp-google-analytics:*)

## Примеры использования

```
Show me active users by country for the last 7 days
```

```
Send a purchase event for order #12345, $99.99 USD
```

## Ресурсы

- [GitHub Repository](https://github.com/gomakers-ai/mcp-google-analytics)

## Примечания

Важно: Отчеты Google Analytics могут возвращать большие наборы данных, которые потребляют значительное количество токенов. Все инструменты чтения по умолчанию возвращают 10 результатов. Используйте конкретные диапазоны дат и выбирайте только нужные измерения/метрики. Проверьте TOKEN_OPTIMIZATION.md для лучших практик. Требует разные учетные данные для чтения данных (Сервисный аккаунт) и отправки событий (Measurement ID + API Secret).