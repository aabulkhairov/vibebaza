---
title: ZincBind MCP сервер
description: MCP сервер, который предоставляет доступ к ZincBindDB GraphQL API для запросов структур сайтов связывания цинка и белковых данных из всеобъемлющей базы данных сайтов связывания цинка.
tags:
- Database
- API
- Cloud
- Analytics
author: QuentinCody
featured: false
---

MCP сервер, который предоставляет доступ к ZincBindDB GraphQL API для запросов структур сайтов связывания цинка и белковых данных из всеобъемлющей базы данных сайтов связывания цинка.

## Установка

### Из исходного кода

```bash
git clone <this-repository>
cd zincbind-mcp-server
npm install
npm run dev
```

### Деплой на Cloudflare Workers

```bash
wrangler auth login
npm run deploy
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "zincbind": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://zincbind-mcp-server.quentincody.workers.dev/sse"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `zincbind_db_graphql_query` | Выполнение GraphQL запросов к ZincBindDB API |

## Возможности

- Запросы сайтов связывания цинка из структур белков
- Доступ к записям PDB (Protein Data Bank) с координацией цинка
- Поиск мультиметаллических сайтов и кластеров цепей
- Исследование лигандирующих остатков и геометрий связывания
- Возможности интроспекции схемы
- Работает на Cloudflare Workers
- Доступ к GraphQL API

## Примеры использования

```
List zinc binding sites
```

```
Query specific PDB structure information
```

```
Perform schema introspection on the ZincBindDB
```

```
Find sites associated with specific protein structures
```

```
Explore zinc coordination patterns in proteins
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/zincbind-mcp-server)

## Примечания

Требуется Node.js v18+, аккаунт Cloudflare для деплоя и Wrangler CLI. Доступен под лицензией MIT с требованием академического цитирования для исследовательского использования. Сервер работает по адресу localhost:8787/sse для разработки и по развернутому URL для продакшена.