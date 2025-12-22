---
title: Shopify MCP сервер
description: MCP сервер для Shopify API, который обеспечивает взаимодействие с данными магазина через GraphQL API, предоставляя инструменты для управления товарами, клиентами, заказами и многим другим.
tags:
- CRM
- API
- Integration
- Productivity
author: GeLi2001
featured: true
---

MCP сервер для Shopify API, который обеспечивает взаимодействие с данными магазина через GraphQL API, предоставляя инструменты для управления товарами, клиентами, заказами и многим другим.

## Установка

### NPX

```bash
npx shopify-mcp --accessToken <YOUR_ACCESS_TOKEN> --domain <YOUR_SHOP>.myshopify.com
```

### NPX с переменными окружения

```bash
npx shopify-mcp
```

### Глобальная установка

```bash
npm install -g shopify-mcp
shopify-mcp --accessToken=<YOUR_ACCESS_TOKEN> --domain=<YOUR_SHOP>.myshopify.com
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "shopify": {
      "command": "npx",
      "args": [
        "shopify-mcp",
        "--accessToken",
        "<YOUR_ACCESS_TOKEN>",
        "--domain",
        "<YOUR_SHOP>.myshopify.com"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-products` | Получить все товары или найти по названию с опциональным лимитом |
| `get-product-by-id` | Получить конкретный товар по ID |
| `createProduct` | Создать новый товар в магазине с названием, описанием, поставщиком, типом, тегами и статусом |
| `get-customers` | Получить клиентов или найти по имени/email с опциональным лимитом |
| `update-customer` | Обновить информацию о клиенте, включая имя, email, телефон, теги, заметки и метаполя |
| `get-customer-orders` | Получить заказы конкретного клиента |
| `get-orders` | Получить заказы с опциональной фильтрацией по статусу и лимитом |
| `get-order-by-id` | Получить конкретный заказ по ID |
| `update-order` | Обновить существующий заказ с тегами, email, заметками, кастомными атрибутами, метаполями и доставкой... |

## Возможности

- Управление товарами: поиск и получение информации о товарах
- Управление клиентами: загрузка данных клиентов и управление тегами клиентов
- Управление заказами: расширенные запросы и фильтрация заказов
- GraphQL интеграция: прямая интеграция с Shopify GraphQL Admin API
- Комплексная обработка ошибок: понятные сообщения об ошибках для API и проблем с аутентификацией

## Переменные окружения

### Обязательные
- `SHOPIFY_ACCESS_TOKEN` - Ваш токен доступа кастомного приложения Shopify
- `MYSHOPIFY_DOMAIN` - Домен вашего магазина Shopify (например, your-store.myshopify.com)

## Ресурсы

- [GitHub Repository](https://github.com/GeLi2001/shopify-mcp)

## Примечания

Требуется токен доступа кастомного приложения Shopify со специальными правами доступа: read_products, write_products, read_customers, write_customers, read_orders, write_orders. Важно: используйте команду 'shopify-mcp', а не 'shopify-mcp-server'. Название пакета - 'shopify-mcp'.