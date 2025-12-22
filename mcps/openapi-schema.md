---
title: OpenAPI Schema MCP сервер
description: Сервер Model Context Protocol, который предоставляет информацию о схемах OpenAPI для LLM, позволяя им исследовать и понимать спецификации API через специализированные инструменты.
tags:
- API
- Integration
- Code
- Productivity
author: hannesj
featured: false
install_command: claude mcp add openapi-schema npx -y mcp-openapi-schema
---

Сервер Model Context Protocol, который предоставляет информацию о схемах OpenAPI для LLM, позволяя им исследовать и понимать спецификации API через специализированные инструменты.

## Установка

### NPX

```bash
# Use the default openapi.yaml in current directory
npx -y mcp-openapi-schema

# Use a specific schema file (relative path)
npx -y mcp-openapi-schema ../petstore.json

# Use a specific schema file (absolute path)
npx -y mcp-openapi-schema /absolute/path/to/api-spec.yaml

# Show help
npx -y mcp-openapi-schema --help
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "OpenAPI Schema": {
      "command": "npx",
      "args": ["-y", "mcp-openapi-schema", "/ABSOLUTE/PATH/TO/openapi.yaml"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list-endpoints` | Выводит все пути API и их HTTP методы с кратким описанием в структуре вложенных объектов |
| `get-endpoint` | Получает подробную информацию о конкретном эндпоинте, включая параметры и ответы |
| `get-request-body` | Получает схему тела запроса для конкретного эндпоинта и метода |
| `get-response-schema` | Получает схему ответа для конкретного эндпоинта, метода и кода статуса |
| `get-path-parameters` | Получает параметры для конкретного пути |
| `list-components` | Выводит все компоненты схемы (схемы, ответы, параметры и т.д.) |
| `get-component` | Получает подробное определение для конкретного компонента |
| `list-security-schemes` | Выводит все доступные схемы безопасности |
| `get-examples` | Получает примеры для конкретного компонента или эндпоинта |
| `search-schema` | Выполняет поиск по путям, операциям и схемам |

## Возможности

- Загрузка любого файла схемы OpenAPI (JSON или YAML), указанного через аргумент командной строки
- Исследование путей API, операций, параметров и схем
- Просмотр подробных схем запросов и ответов
- Поиск определений компонентов и примеров
- Поиск по всей спецификации API
- Получение ответов в формате YAML для лучшего понимания LLM

## Примеры использования

```
What endpoints are available in this API?
```

```
Show me the details for the POST /pets endpoint.
```

```
What parameters does the GET /pets/{petId} endpoint take?
```

```
What is the request body schema for creating a new pet?
```

```
What response will I get from the DELETE /pets/{petId} endpoint?
```

## Ресурсы

- [GitHub Repository](https://github.com/hannesj/mcp-openapi-schema)

## Примечания

Расположение файлов конфигурации: macOS/Linux: ~/Library/Application Support/Claude/claude_desktop_config.json, Windows: $env:AppData\Claude\claude_desktop_config.json. Используйте флаг -s или --scope с project (по умолчанию) или global для указания области хранения конфигурации.