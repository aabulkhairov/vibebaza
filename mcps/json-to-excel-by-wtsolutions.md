---
title: JSON to Excel by WTSolutions MCP сервер
description: MCP сервер, который конвертирует JSON данные в CSV формат, поддерживая как прямые строки JSON данных, так и JSON файлы по URL.
tags:
- API
- Productivity
- Integration
- Analytics
author: he-yang
featured: false
---

MCP сервер, который конвертирует JSON данные в CSV формат, поддерживая как прямые строки JSON данных, так и JSON файлы по URL.

## Установка

### NPX

```bash
npx mcp-remote https://mcp2.wtsolutions.cn/sse --transport sse-only
```

## Конфигурация

### Конфигурация NPX

```json
{
  "mcpServers": {
    "json_to_excel": {
      "args": [
        "mcp-remote",
        "https://mcp2.wtsolutions.cn/sse",
        "--transport",
        "sse-only"
      ],
      "command": "npx"
    }
  }
}
```

### Конфигурация SSE

```json
{
  "mcpServers": {
    "json2excelsse": {
      "type": "sse",
      "url": "https://mcp2.wtsolutions.cn/sse"
    }
  }
}
```

### Конфигурация Streamable HTTP

```json
{
  "mcpServers": {
    "json2excelmcp": {
      "type": "streamableHttp",
      "url": "https://mcp2.wtsolutions.cn/mcp"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `json_to_excel_mcp_from_data` | Конвертирует строку JSON данных в строку CSV формата |
| `json_to_excel_mcp_from_url` | Конвертирует JSON файл по предоставленному URL (.json формат) в строку CSV формата |

## Возможности

- Конвертация строк JSON данных в CSV формат
- Конвертация JSON файлов по URL в CSV формат
- Автоматическая обработка типов данных (числа, булевы значения, строки, массивы, объекты)
- Поддержка как JSON массивов, так и отдельных объектов
- CSV заголовки генерируются из ключей JSON объектов
- Множественные транспортные протоколы (SSE, Streamable HTTP)

## Примеры использования

```
Convert the following JSON data into CSV format: [{"Name": "John Doe", "Age": 25, "IsStudent": false}, {"Name": "Jane Smith", "Age": 30, "IsStudent": true}]
```

```
Convert the following JSON object into CSV format: {"Name": "John Doe", "Age": 25, "IsStudent": false, "Courses": ["Math", "Science"]}
```

```
Convert JSON file to Excel, file URL: https://mcp.wtsolutions.cn/example.json
```

```
I've just uploaded one .json file to you, please extract its URL and send it to MCP tool 'json_to_excel_mcp_from_url', for JSON to Excel conversion.
```

## Ресурсы

- [GitHub Repository](https://github.com/he-yang/json-to-excel-mcp)

## Примечания

Часть набора инструментов JSON to Excel от WTSolutions. Бесплатно на данный момент. Поддерживает множественные транспортные протоколы, включая SSE и Streamable HTTP. Возвращает структурированный ответ с полями isError, msg и data. Включает комплексную обработку ошибок для невалидного JSON, сетевых ошибок и сценариев "файл не найден".