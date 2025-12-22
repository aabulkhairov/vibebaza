---
title: Lark(Feishu) MCP сервер
description: MCP сервер для работы с таблицами, сообщениями, документами и другими возможностями Lark(Feishu), обеспечивающий интеграцию с продуктивными инструментами Lark.
tags:
- Productivity
- Integration
- API
- Storage
author: kone-net
featured: false
---

MCP сервер для работы с таблицами, сообщениями, документами и другими возможностями Lark(Feishu), обеспечивающий интеграцию с продуктивными инструментами Lark.

## Установка

### UVX

```bash
uvx parent_of_servers_repo/servers/src/mcp_server_lark
```

## Конфигурация

### Конфигурация MCP сервера

```json
"mcpServers": {
  "mcpServerLark": {
    "description": "MCP Server For Lark(Feishu)",
    "command": "uvx",
    "args": [
      "parent_of_servers_repo/servers/src/mcp_server_lark"
    ],
    "env": {
        "LARK_APP_ID": "xxx",
        "LARK_APP_SECRET": "xxx"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `write_excel` | Записывает данные в таблицу Lark(Feishu) и возвращает ссылку. Необходимо предоставить email для добавления... |

## Возможности

- Запись данных в таблицы Lark(Feishu)
- Создание ссылок для совместного доступа к таблицам
- Контроль доступа через email разрешения
- Интеграция с Lark Open Platform

## Переменные окружения

### Обязательные
- `LARK_APP_ID` - Ваш ID приложения Lark из Lark Open Platform
- `LARK_APP_SECRET` - Ваш секретный ключ приложения Lark из Lark Open Platform

## Ресурсы

- [GitHub Repository](https://github.com/kone-net/mcp_server_lark)

## Примечания

Требует создания приложения Lark(Feishu) на https://open.larkoffice.com/app и получения разрешения 'sheets:spreadsheet:readonly'. MIT License.