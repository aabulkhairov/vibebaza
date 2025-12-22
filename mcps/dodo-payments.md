---
title: Dodo Payments MCP сервер
description: TypeScript MCP сервер, который позволяет AI агентам безопасно выполнять платежные операции через легковесный, совместимый с serverless интерфейс к Dodo Payments API.
tags:
- API
- Finance
- Integration
- Code
- Analytics
author: dodopayments
featured: false
install_command: claude mcp add --transport stdio dodopayments_api --env DODO_PAYMENTS_API_KEY="Your
  DODO_PAYMENTS_API_KEY here." DODO_PAYMENTS_WEBHOOK_KEY="Your DODO_PAYMENTS_WEBHOOK_KEY
  here." -- npx -y dodopayments-mcp
---

TypeScript MCP сервер, который позволяет AI агентам безопасно выполнять платежные операции через легковесный, совместимый с serverless интерфейс к Dodo Payments API.

## Установка

### NPX напрямую

```bash
export DODO_PAYMENTS_API_KEY="My Bearer Token"
export DODO_PAYMENTS_WEBHOOK_KEY="My Webhook Key"
export DODO_PAYMENTS_ENVIRONMENT="live_mode"
npx -y dodopayments-mcp@latest
```

### Удаленный HTTP

```bash
--transport=http --port=3000
```

## Конфигурация

### MCP Client JSON

```json
{
  "mcpServers": {
    "dodopayments_api": {
      "command": "npx",
      "args": ["-y", "dodopayments-mcp", "--client=claude", "--tools=dynamic"],
      "env": {
        "DODO_PAYMENTS_API_KEY": "My Bearer Token",
        "DODO_PAYMENTS_WEBHOOK_KEY": "My Webhook Key",
        "DODO_PAYMENTS_ENVIRONMENT": "live_mode"
      }
    }
  }
}
```

### Удаленный HTTP сервер

```json
{
  "mcpServers": {
    "dodopayments_api": {
      "url": "http://localhost:3000",
      "headers": {
        "Authorization": "Bearer <auth value>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `create_checkout_sessions` | Создание сессий оформления заказа для платежей |
| `retrieve_checkout_sessions` | Получение информации о сессиях оформления заказа |
| `create_payments` | Создание новых платежей |
| `list_payments` | Список существующих платежей |
| `create_subscriptions` | Создание новых подписок |
| `update_subscriptions` | Обновление существующих подписок |
| `list_subscriptions` | Список всех подписок |
| `retrieve_usage_history_subscriptions` | Получение детальной истории использования для подписок с оплатой по использованию |
| `create_customers` | Создание новых клиентов |
| `list_customers` | Список существующих клиентов |
| `create_refunds` | Создание возвратов платежей |
| `list_disputes` | Список спорных платежей |
| `create_products` | Создание новых продуктов |
| `list_products` | Список всех продуктов |
| `create_discounts` | Создание скидочных кодов |

## Возможности

- Три режима работы с инструментами: отдельные endpoints, динамическое обнаружение или выполнение кода
- Полный набор платежных операций включая оформление заказов, подписки и возвраты
- Управление клиентами и операции с кошельками
- Управление продуктами и скидками
- Управление и валидация лицензионных ключей
- Конфигурация и управление webhook'ами
- Биллинг и аналитика по использованию
- Отслеживание споров и выплат
- Режимы совместимости для разных клиентов
- Расширенная фильтрация по ресурсам, типу операций и инструментам

## Переменные окружения

### Обязательные
- `DODO_PAYMENTS_API_KEY` - Bearer токен для аутентификации в Dodo Payments API
- `DODO_PAYMENTS_WEBHOOK_KEY` - Ключ для аутентификации webhook'ов

### Опциональные
- `DODO_PAYMENTS_ENVIRONMENT` - Режим окружения (например, live_mode)

## Ресурсы

- [GitHub Repository](https://github.com/dodopayments/dodopayments-node)

## Примечания

Создан с помощью Stainless. Поддерживает фильтрацию по --resource, --operation, --tool с wildcards. Предлагает динамическое обнаружение инструментов для избежания ограничений контекстного окна. Включает Deno sandbox для выполнения кода с сетевым доступом только к базовому URL API. Совместим с множественными MCP клиентами включая Claude, Cursor и VS Code.