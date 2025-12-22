---
title: Splunk MCP сервер
description: Go реализация MCP сервера для Splunk, которая предоставляет доступ к сохраненным поискам, алертам, индексам и макросам через STDIO и SSE транспортные методы.
tags:
- Monitoring
- Analytics
- Security
- DevOps
- Integration
author: Community
featured: false
---

Go реализация MCP сервера для Splunk, которая предоставляет доступ к сохраненным поискам, алертам, индексам и макросам через STDIO и SSE транспортные методы.

## Установка

### Smithery

```bash
Available at Smithery: https://smithery.ai/server/@jkosik/mcp-server-splunk
```

### Docker

```bash
docker build -t mcp-server-splunk .

echo '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}' | \
docker run --rm -i \
  -e SPLUNK_URL=https://your-splunk-instance:8089 \
  -e SPLUNK_TOKEN=your-splunk-token \
  mcp-server-splunk | jq
```

### Из исходного кода

```bash
go build -o cmd/mcp-server-splunk/mcp-server-splunk cmd/mcp-server-splunk/main.go
```

## Конфигурация

### Cursor STDIO

```json
{
  "mcpServers": {
    "splunk_stdio": {
      "name": "Splunk MCP Server (STDIO)",
      "description": "MCP server for Splunk integration",
      "type": "stdio",
      "command": "/Users/juraj/data/github.com/jkosik/mcp-server-splunk/cmd/mcp-server-splunk/mcp-server-splunk",
      "env": {
        "SPLUNK_URL": "https://your-splunk-instance:8089",
        "SPLUNK_TOKEN": "your-splunk-token"
      }
    }
  }
}
```

### Cursor SSE

```json
{
  "mcpServers": {
    "splunk_sse": {
      "name": "Splunk MCP Server (SSE)",
      "description": "MCP server for Splunk integration (SSE mode)",
      "type": "sse",
      "url": "http://localhost:3001/sse"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_splunk_saved_searches` | Получает список сохраненных поисков Splunk с поддержкой пагинации |
| `list_splunk_alerts` | Получает список алертов Splunk с фильтрацией по заголовку и пагинацией |
| `list_splunk_fired_alerts` | Получает список сработавших алертов с фильтрацией по имени поиска и временному диапазону |
| `list_splunk_indexes` | Получает список индексов Splunk с пагинацией |
| `list_splunk_macros` | Получает список макросов Splunk с пагинацией |

## Возможности

- Поддержка STDIO и SSE транспортных методов
- Поддержка пагинации для всех инструментов с настраиваемым количеством и смещением
- Фильтрация алертов по паттернам заголовка и имени поиска
- Фильтрация по временному диапазону для сработавших алертов
- MCP Prompt для поиска алертов по ключевому слову
- MCP Resource с локальным CSV файлом для контекста Splunk
- Построен с использованием github.com/mark3labs/mcp-go SDK

## Переменные окружения

### Обязательные
- `SPLUNK_URL` - URL вашего экземпляра Splunk (например, https://your-splunk-instance:8089)
- `SPLUNK_TOKEN` - Ваш токен аутентификации Splunk

## Примеры использования

```
How many MCP tools for Splunk are available?
```

```
How many Splunk indexes do we have?
```

```
Can you list first 5 Splunk macros including underlying queries?
```

```
How many alerts with "Alert_CRITICAL" in the name were fired in the last day?
```

```
Read the MCP Resource "Data Dictionary" and find the contact person for the Splunk index XYZ.
```

## Ресурсы

- [GitHub Repository](https://github.com/jkosik/mcp-server-splunk)

## Примечания

Сертифицирован MCP Review: https://mcpreview.com/mcp-servers/jkosik/mcp-server-splunk. Сервер включает демо GIF, показывающий интеграцию с Cursor. Все инструменты поддерживают пагинацию с максимум 100 результатами на вызов.