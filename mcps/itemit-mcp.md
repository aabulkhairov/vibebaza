---
title: itemit MCP сервер
description: MCP сервер, который предоставляет возможности отслеживания активов через подключение к платформе управления активами itemit, позволяя пользователям искать, создавать и управлять активами и локациями программным способом.
tags:
- API
- Productivity
- Integration
- Monitoring
author: umin-ai
featured: false
---

MCP сервер, который предоставляет возможности отслеживания активов через подключение к платформе управления активами itemit, позволяя пользователям искать, создавать и управлять активами и локациями программным способом.

## Установка

### Из исходного кода

```bash
npm install
npm run build
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "mcpServers": {
    "itemit-mcp": {
      "disabled": false,
      "timeout": 60,
      "type": "stdio",
      "command": "node",
      "args": [
        "/Users/<user>/Documents/itemit-mcp/build/index.js"
      ],
      "env": {
        "ITEMIT_API_KEY": "<YOUR_API_KEY>",
        "ITEMIT_USER_ID": "<YOUR_USER_ID>",
        "ITEMIT_USER_TOKEN": "<YOUR_USER_TOKEN>",
        "ITEMIT_WORKSPACE_ID": "<YOUR_WORKSPACE_ID>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-location-by-name` | Получить локации по имени в itemit |
| `search-item-by-name` | Поиск элементов по имени в itemit |
| `create-item` | Создать элемент в itemit |
| `get-reminders` | Получить напоминания из itemit |
| `get-items` | Получить элементы из itemit |

## Возможности

- Поиск и получение активов по имени
- Создание новых элементов с описанием и серийными номерами
- Поиск локаций со списками элементов
- Получение списка элементов с пагинацией
- Получение напоминаний с платформы itemit
- Интеграция с API управления активами itemit

## Переменные окружения

### Обязательные
- `ITEMIT_API_KEY` - Ваш API ключ itemit
- `ITEMIT_USER_ID` - Ваш ID пользователя itemit
- `ITEMIT_USER_TOKEN` - Ваш токен пользователя itemit
- `ITEMIT_WORKSPACE_ID` - Ваш ID рабочего пространства itemit

## Примеры использования

```
Search for a laptop in the inventory
```

```
Find items in the warehouse location
```

```
Create a new projector asset with serial number
```

```
Get a list of all items with pagination
```

## Ресурсы

- [GitHub Repository](https://github.com/umin-ai/itemit-mcp)

## Примечания

Разработан и поддерживается командой uminai MCP. Требует аккаунт itemit.com для получения учетных данных API. Поддерживает пагинацию для больших наборов данных и следует модели данных itemit API для ответов.