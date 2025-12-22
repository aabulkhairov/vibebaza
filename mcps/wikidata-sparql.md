---
title: Wikidata SPARQL MCP сервер
description: MCP сервер, предоставляющий доступ к графу знаний Wikidata через SPARQL запросы, развернутый на Cloudflare Workers с поддержкой как Server-Sent Events, так и HTTP транспорта.
tags:
- Database
- API
- Analytics
- Search
- Cloud
author: QuentinCody
featured: false
---

MCP сервер, предоставляющий доступ к графу знаний Wikidata через SPARQL запросы, развернутый на Cloudflare Workers с поддержкой как Server-Sent Events, так и HTTP транспорта.

## Установка

### Деплой на Cloudflare Workers

```bash
git clone https://github.com/QuentinCody/wikidata-sparql-mcp-server.git
cd wikidata-sparql-mcp-server
npm install
npm run deploy
```

### Локальная разработка

```bash
npm install
npm start  # Запускается на http://localhost:8787
```

### NPX удаленно

```bash
npx mcp-remote https://wikidata-sparql-mcp-server.<your-account>.workers.dev/sse
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "wikidata-sparql": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://wikidata-sparql-mcp-server.<your-account>.workers.dev/sse"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `sparql_query` | Выполнение SPARQL запросов к графу знаний Wikidata с поддержкой как интроспекции, так и... |

## Возможности

- Единый универсальный инструмент SPARQL запросов для всех операций
- Полная поддержка SPARQL для графа знаний Wikidata
- Множественные форматы вывода: JSON, XML, Turtle и CSV
- Защита от таймаутов с настраиваемыми таймаутами (1-60 секунд)
- Удаленный деплой на Cloudflare Workers для глобальной доступности
- Поддержка двух типов транспорта: как SSE, так и HTTP эндпоинты
- Комплексная обработка ошибок с валидацией SPARQL
- Сетевая устойчивость при недоступности эндпоинта Wikidata

## Примеры использования

```
Find 10 famous scientists with their birth dates
```

```
Get all programming languages and their creators
```

```
Find Nobel Prize winners in Physics
```

```
List countries and their capitals
```

```
Find software companies founded after 2000
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/wikidata-sparql-mcp-server)

## Примечания

Сервер работает на Cloudflare Workers и предоставляет доступ к SPARQL эндпоинту Wikidata. Он поддерживает как интроспективные запросы для понимания структуры графа знаний, так и запросы данных для получения конкретной информации. Сервер включает комплексные примеры запросов для исследований, географии и технологических кейсов.