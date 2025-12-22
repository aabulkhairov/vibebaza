---
title: GraphQL Schema MCP сервер
description: MCP сервер, который предоставляет LLM информацию о GraphQL схемах, позволяя им исследовать и понимать GraphQL схемы через специализированные инструменты.
tags:
- API
- Code
- Database
- Integration
author: Community
featured: false
install_command: claude mcp add graphql-schema npx -y mcp-graphql-schema
---

MCP сервер, который предоставляет LLM информацию о GraphQL схемах, позволяя им исследовать и понимать GraphQL схемы через специализированные инструменты.

## Установка

### NPX

```bash
# Use the default schema.graphqls in current directory
npx -y mcp-graphql-schema

# Use a specific schema file (relative path)
npx -y mcp-graphql-schema ../schema.shopify.2025-01.graphqls

# Use a specific schema file (absolute path)
npx -y mcp-graphql-schema /absolute/path/to/schema.graphqls
```

### Smithery

```bash
npx -y @smithery/cli install @hannesj/mcp-graphql-schema --client claude
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "GraphQL Schema": {
      "command": "npx",
      "args": ["-y", "mcp-graphql-schema", "/ABSOLUTE/PATH/TO/schema.graphqls"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list-query-fields` | Показывает все доступные поля корневого уровня для GraphQL запросов |
| `get-query-field` | Получает детальное описание для конкретного поля запроса в формате SDL |
| `list-mutation-fields` | Показывает все доступные поля корневого уровня для GraphQL мутаций |
| `get-mutation-field` | Получает детальное описание для конкретного поля мутации в формате SDL |
| `list-subscription-fields` | Показывает все доступные поля корневого уровня для GraphQL подписок (если присутствуют в схеме) |
| `get-subscription-field` | Получает детальное описание для конкретного поля подписки (если присутствует в схеме) |
| `list-types` | Показывает все типы, определенные в GraphQL схеме (исключая внутренние типы) |
| `get-type` | Получает детальное описание для конкретного GraphQL типа в формате SDL |
| `get-type-fields` | Получает упрощенный список полей с их типами для конкретного GraphQL объектного типа |
| `search-schema` | Ищет типы или поля в схеме по шаблону имени (нечувствительный к регистру regex) |

## Возможности

- Загрузка любого файла GraphQL схемы, указанного через аргумент командной строки
- Исследование полей запросов, мутаций и подписок
- Поиск детальных определений типов
- Поиск типов и полей с использованием сопоставления шаблонов
- Получение упрощенной информации о полях, включая типы и аргументы
- Фильтрация внутренних GraphQL типов для более чистых результатов

## Примеры использования

```
What query fields are available in this GraphQL schema?
```

```
Show me the details of the "user" query field.
```

```
What mutation operations can I perform in this schema?
```

```
List all types defined in this schema.
```

```
Show me the definition of the "Product" type.
```

## Ресурсы

- [GitHub Repository](https://github.com/hannesj/mcp-graphql-schema)

## Примечания

Расположение конфигурационных файлов: macOS/Linux: ~/Library/Application Support/Claude/claude_desktop_config.json, Windows: $env:AppData\Claude\claude_desktop_config.json. Можно добавить несколько MCP серверов для разных схем с разными именами.