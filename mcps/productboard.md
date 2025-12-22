---
title: Productboard MCP сервер
description: MCP сервер, который интегрирует Productboard API в агентские рабочие процессы, предоставляя доступ к данным компаний, компонентов, функций, заметок и продуктов.
tags:
- API
- Integration
- Productivity
- CRM
- Analytics
author: Community
featured: false
---

MCP сервер, который интегрирует Productboard API в агентские рабочие процессы, предоставляя доступ к данным компаний, компонентов, функций, заметок и продуктов.

## Установка

### NPX

```bash
npx -y productboard-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "productboard": {
      "command": "npx",
      "args": [
        "-y",
        "productboard-mcp"
      ],
      "env": {
        "PRODUCTBOARD_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_companies` | Получить данные компаний из Productboard |
| `get_company_detail` | Получить детальную информацию о конкретной компании |
| `get_components` | Получить данные компонентов из Productboard |
| `get_component_detail` | Получить детальную информацию о конкретном компоненте |
| `get_features` | Получить данные функций из Productboard |
| `get_feature_detail` | Получить детальную информацию о конкретной функции |
| `get_feature_statuses` | Получить статусы функций из Productboard |
| `get_notes` | Получить данные заметок из Productboard |
| `get_products` | Получить данные продуктов из Productboard |
| `get_product_detail` | Получить детальную информацию о конкретном продукте |

## Возможности

- Доступ к компаниям Productboard и детальной информации о компаниях
- Получение компонентов и информации о компонентах
- Доступ к функциям, деталям функций и статусам функций
- Получение заметок из Productboard
- Доступ к продуктам и деталям продуктов

## Переменные окружения

### Обязательные
- `PRODUCTBOARD_ACCESS_TOKEN` - Токен доступа для аутентификации в Productboard API

## Ресурсы

- [GitHub Repository](https://github.com/kenjihikmatullah/productboard-mcp)

## Примечания

Требует получения токена доступа от Productboard в соответствии с их руководством по аутентификации. Лицензия MIT License.