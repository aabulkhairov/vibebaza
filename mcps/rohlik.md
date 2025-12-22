---
title: Rohlik MCP сервер
description: MCP сервер, который позволяет AI-ассистентам взаимодействовать с сервисами доставки продуктов Rohlik Group в нескольких странах, предоставляя инструменты для поиска товаров, управления корзиной покупок и доступа к информации аккаунта.
tags:
- API
- Integration
- Productivity
- Web Scraping
author: tomaspavlin
featured: false
---

MCP сервер, который позволяет AI-ассистентам взаимодействовать с сервисами доставки продуктов Rohlik Group в нескольких странах, предоставляя инструменты для поиска товаров, управления корзиной покупок и доступа к информации аккаунта.

## Установка

### NPX

```bash
npx -y @tomaspavlin/rohlik-mcp
```

### Из исходного кода

```bash
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "rohlik": {
      "command": "npx",
      "args": ["-y", "@tomaspavlin/rohlik-mcp"],
      "env": {
        "ROHLIK_USERNAME": "your-email@example.com",
        "ROHLIK_PASSWORD": "your-password",
        "ROHLIK_BASE_URL": "https://www.rohlik.cz"
      }
    }
  }
}
```

### Локальная разработка

```json
{
  "mcpServers": {
    "rohlik-local": {
      "command": "node",
      "args": ["/path/to/rohlik-mcp/dist/index.js"],
      "env": {
        "ROHLIK_USERNAME": "your-email@example.com",
        "ROHLIK_PASSWORD": "your-password",
        "ROHLIK_BASE_URL": "https://www.rohlik.cz"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_products` | Поиск продуктов по названию с возможностями фильтрации |
| `add_to_cart` | Добавление нескольких товаров в корзину покупок |
| `get_cart_content` | Просмотр содержимого корзины и итоговых сумм |
| `remove_from_cart` | Удаление товаров из корзины покупок |
| `get_shopping_list` | Получение списков покупок по ID |
| `get_meal_suggestions` | Получение персонализированных предложений для завтрака, обеда, ужина, перекусов, выпечки, напитков или здорового питания... |
| `get_frequent_items` | Анализ истории заказов для поиска наиболее часто покупаемых товаров (общий + по категориям) |
| `get_shopping_scenarios` | Интерактивное руководство, показывающее возможности MCP |
| `get_account_data` | Получение полной информации об аккаунте, включая детали доставки, заказы, уведомления, корзину и... |
| `get_order_history` | Просмотр истории доставленных заказов с деталями |
| `get_order_detail` | Получение подробной информации о конкретном заказе, включая все товары |
| `get_upcoming_orders` | Просмотр запланированных предстоящих заказов |
| `get_delivery_info` | Получение текущей информации о доставке и тарифах |
| `get_delivery_slots` | Просмотр доступных временных слотов доставки для вашего адреса |
| `get_premium_info` | Проверка статуса подписки Rohlik Premium и льгот |

## Возможности

- Поддержка нескольких регионов Rohlik (Чехия, Германия, Австрия, Венгрия, Румыния, с планируемыми Италией и Испанией)
- Умные покупки с персонализированными предложениями блюд на основе истории заказов
- Анализ частоты покупаемых товаров
- Полное управление корзиной покупок
- История заказов и отслеживание доставки
- Мониторинг статуса подписки Premium
- Отслеживание экологического воздействия с многоразовыми пакетами
- Полная информация об аккаунте и доставке
- Поиск товаров с возможностями фильтрации

## Переменные окружения

### Обязательные
- `ROHLIK_USERNAME` - Email-адрес вашего аккаунта Rohlik
- `ROHLIK_PASSWORD` - Пароль от вашего аккаунта Rohlik

### Опциональные
- `ROHLIK_BASE_URL` - Базовый URL для региона Rohlik (по умолчанию https://www.rohlik.cz)
- `ROHLIK_DEBUG` - Включить режим отладки для просмотра подробных логов

## Примеры использования

```
Add ingredients for apple pie to the cart. Only gluten-free and budget-friendly.
```

```
Or actually, instead of apple pie I want to make pumpkin pie. Change the ingredients.
```

```
What are the items in my cart?
```

```
Add the items in the attached shopping list photo to the cart.
```

```
Add the bread I marked as favorite in Rohlik to my cart.
```

## Ресурсы

- [GitHub Repository](https://github.com/tomaspavlin/rohlik-mcp)

## Примечания

Этот MCP сервер создан в учебных целях с использованием обратно спроектированного API Rohlik и предназначен только для личного использования. Включает полный набор тестов и инструменты валидации API. Поддерживает множество опций отладки и подробное логирование для устранения неполадок.