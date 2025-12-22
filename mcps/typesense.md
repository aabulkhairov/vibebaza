---
title: Typesense MCP сервер
description: Реализация сервера Model Context Protocol (MCP), который предоставляет AI-моделям доступ к возможностям поиска Typesense, позволяя LLM находить, искать и анализировать данные, хранящиеся в коллекциях Typesense.
tags:
- Search
- Database
- Analytics
- AI
- Integration
author: suhail-ak-s
featured: false
---

Реализация сервера Model Context Protocol (MCP), который предоставляет AI-моделям доступ к возможностям поиска Typesense, позволяя LLM находить, искать и анализировать данные, хранящиеся в коллекциях Typesense.

## Установка

### NPM Global

```bash
npm install -g typesense-mcp-server
```

### NPM Local

```bash
npm install typesense-mcp-server
```

### mcp-get

```bash
npx @michaellatman/mcp-get@latest install typesense-mcp-server
```

## Конфигурация

### Claude Desktop - Development

```json
{
  "mcpServers": {
    "typesense": {
      "command": "node",
      "args": [
        "~/typesense-mcp-server/dist/index.js",
        "--host", "your-typesense-host",
        "--port", "8108",
        "--protocol", "http",
        "--api-key", "your-api-key"
      ]
    }
  }
}
```

### Claude Desktop - NPX

```json
{
  "mcpServers": {
    "typesense": {
      "command": "npx",
      "args": [
        "-y",
        "typesense-mcp-server",
        "--host", "your-typesense-host",
        "--port", "8108",
        "--protocol", "http",
        "--api-key", "your-api-key"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `typesense_query` | Поиск документов в коллекциях Typesense с мощной фильтрацией, включая текст запроса, колл... |
| `typesense_get_document` | Получение конкретных документов по ID из коллекций, возвращающее полные данные документа |
| `typesense_collection_stats` | Получение статистики о коллекции Typesense, включая метаданные, количество документов и информацию о схеме... |
| `typesense_list_collections` | Список всех доступных коллекций с их схемами, обеспечивающий обнаружение без конфигурации и маршрутизацию с ... |

## Возможности

- Список и доступ к коллекциям через typesense:// URI с именем, описанием и количеством документов
- Полнотекстовый поиск с настраиваемыми параметрами, фильтрацией, сортировкой и пагинацией
- Получение документов по ID с полными данными документа
- Статистика коллекций и анализ метаданных
- Обнаружение без конфигурации и маршрутизация для динамического перечисления коллекций
- Вывод схемы с поддержкой полей для поиска, фасетирования и числовых полей
- JSON mime type для доступа к схеме
- Анализ структуры и содержимого коллекций с инсайтами
- Предложения по поиску для эффективных стратегий запросов

## Примеры использования

```
Анализ структуры и содержимого коллекции для конкретной коллекции
```

```
Получение предложений для эффективных поисковых запросов для коллекции
```

```
Поиск документов с показателями релевантности и фильтрацией
```

```
Получение конкретных документов по их ID
```

```
Получение подробной статистики о метаданных коллекции и схеме
```

## Ресурсы

- [GitHub Repository](https://github.com/suhail-ak-s/mcp-typesense-server)

## Примечания

Сервер записывает информацию в /tmp/typesense-mcp.log и предоставляет подсказки для analyze_collection и search_suggestions. Ресурсы включают схемы коллекций, доступные через typesense://collections/<collection> URI. Для отладки используйте MCP Inspector с командой 'npm run inspector'.