---
title: Shopify Storefront MCP сервер
description: Предоставляет доступ к Shopify Storefront API через MCP, позволяя AI-ассистентам запрашивать и взаимодействовать с данными Shopify магазина, включая товары, коллекции, инвентарь и управление корзиной.
tags:
- API
- Integration
- Web Scraping
- Productivity
author: QuentinCody
featured: false
---

Предоставляет доступ к Shopify Storefront API через MCP, позволяя AI-ассистентам запрашивать и взаимодействовать с данными Shopify магазина, включая товары, коллекции, инвентарь и управление корзиной.

## Установка

### Из исходников

```bash
1. Clone this repository
2. Install dependencies: `pip install -r requirements.txt`
3. Copy `.env.example` to `.env` and configure your environment variables
4. Generate a Storefront API token via Shopify Admin
5. Run the server: `python -m shopify_storefront_mcp_server`
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `shopify_discover` | Определяет, принадлежит ли URL витрине Shopify и обнаруживает токены аутентификации |
| `shopify_storefront_graphql` | Выполняет GraphQL запросы к Storefront API |
| `customer_data` | Универсальный инструмент для всех операций с данными клиентов (создание, чтение, обновление, удаление) |

## Возможности

- Доступ к данным о товарах, коллекциях и инвентаре
- Создание и управление корзиной
- Поддержка GraphQL запросов и мутаций
- Автоматическая обработка и валидация токенов
- Простая интеграция с AI-ассистентами, совместимыми с MCP
- Управление данными клиентов с CRUD операциями
- MCP ресурсы для информации о клиентах
- Поддержка кастомных полей и персонализации
- Создание чекаута с интеграцией данных клиентов

## Переменные окружения

### Обязательные
- `SHOPIFY_STOREFRONT_ACCESS_TOKEN` - Ваш токен доступа к Storefront API
- `SHOPIFY_STORE_NAME` - Название вашего магазина (без .myshopify.com)

### Опциональные
- `SHOPIFY_API_VERSION` - Версия API для использования
- `SHOPIFY_BUYER_IP` - IP адрес покупателя

## Примеры использования

```
Get all customer data
```

```
Get a specific customer field like name or shipping address
```

```
Update customer information including addresses
```

```
Add custom fields for AI personalization
```

```
Delete specific customer data fields
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/shopify-storefront-mcp-server)

## Примечания

Данные клиентов хранятся локально в user_data/customer.json и не должны коммититься в систему контроля версий. Серверу требуются права Storefront API, включая unauthenticated_read_product_listings, unauthenticated_read_product_inventory, unauthenticated_read_product_pricing, unauthenticated_write_checkouts и unauthenticated_read_content. Поддерживает как новые (shpsa_), так и старые (shpat_) форматы токенов Storefront API.