---
title: Excel to JSON MCP by WTSolutions MCP сервер
description: MCP сервер, который конвертирует данные Excel (.xlsx) и CSV в формат JSON,
  поддерживая как прямой ввод данных, так и конвертацию файлов по URL с автоматическим
  определением типов данных.
tags:
- Productivity
- API
- Analytics
- Integration
author: Community
featured: false
---

MCP сервер, который конвертирует данные Excel (.xlsx) и CSV в формат JSON, поддерживая как прямой ввод данных, так и конвертацию файлов по URL с автоматическим определением типов данных.

## Установка

### NPX

```bash
npx mcp-remote https://mcp.wtsolutions.cn/sse --transport sse-only
```

## Конфигурация

### Stdio (NPX)

```json
{
  "mcpServers": {
    "excel2json": {
      "args": [
        "mcp-remote",
        "https://mcp.wtsolutions.cn/sse",
        "--transport",
        "sse-only"
      ],
      "command": "npx",
      "tools": [
        "excel_to_json_mcp_from_data",
        "excel_to_json_mcp_from_url"
      ]
    }
  }
}
```

### SSE Transport

```json
{
  "mcpServers": {
    "excel2jsonsse": {
      "type": "sse",
      "url": "https://mcp.wtsolutions.cn/sse"
    }
  }
}
```

### Streamable HTTP

```json
{
  "mcpServers": {
    "excel2jsonmcp": {
      "type": "streamableHttp",
      "url": "https://mcp.wtsolutions.cn/mcp"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `excel_to_json_mcp_from_data` | Конвертирует данные Excel с разделением табуляцией или CSV данные с разделением запятыми в формат JSON |
| `excel_to_json_mcp_from_url` | Конвертирует файл Excel (.xlsx) по указанному URL в формат JSON |

## Возможности

- Конвертирует данные Excel (.xlsx) и CSV в формат JSON
- Поддерживает как прямой ввод данных, так и конвертацию файлов по URL
- Автоматическое определение типов данных (числа, булевы значения, даты, строки)
- Обрабатывает несколько листов Excel со структурированным выводом
- Несколько вариантов транспорта: stdio, SSE и streamable HTTP
- Комплексная обработка ошибок с описательными сообщениями

## Примеры использования

```
Convert the following data into JSON format: Name	Age	IsStudent\nJohn Doe	25	false\nJane Smith	30	true
```

```
Convert the following data into JSON format: Name,Age,IsStudent\nJohn Doe,25,false\nJane Smith,30,true
```

```
Convert Excel file to JSON, file URL: https://tools.wtsolutions.cn/example.xlsx
```

```
I've just uploaded one .xlsx file to you, please extract its URL and send it to MCP tool 'excel_to_json_mcp_from_url', for Excel to JSON conversion.
```

## Ресурсы

- [GitHub Repository](https://github.com/he-yang/excel-to-json-mcp)

## Примечания

Часть экосистемы Excel to JSON by WTSolutions, включающей веб-приложение, надстройку Excel и API. Пока бесплатный с возможностью поддержки донатами. Требует минимум две строки (заголовок + данные) во входных данных. Поддерживает китайскую документацию.