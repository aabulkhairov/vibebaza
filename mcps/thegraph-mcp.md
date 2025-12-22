---
title: thegraph-mcp сервер
description: MCP сервер, который предоставляет AI агентам доступ к индексированным блокчейн данным из The Graph, позволяя выполнять GraphQL запросы к субграфам для блокчейн аналитики.
tags:
- Finance
- Analytics
- API
- Database
author: kukapay
featured: false
---

MCP сервер, который предоставляет AI агентам доступ к индексированным блокчейн данным из The Graph, позволяя выполнять GraphQL запросы к субграфам для блокчейн аналитики.

## Установка

### Из исходного кода

```bash
git clone https://github.com/kukapay/thegraph-mcp.git
```

## Конфигурация

### Конфигурация клиента

```json
{
  "mcpServers": {
    "thegraph-mcp": {
      "command": "uv",
      "args": ["--directory", "path/to/thegraph-mcp", "run", "main.py"],
      "env": {
        "THEGRAPH_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `getSubgraphSchema` | Получает схему указанного субграфа, предоставляя AI агентам контекст, необходимый для генерации... |
| `querySubgraph` | Выполняет GraphQL запросы к указанному субграфу для анализа блокчейн данных |

## Возможности

- Получение схем субграфов в читаемом или JSON формате
- Выполнение GraphQL запросов к субграфам The Graph
- Поддержка анализа блокчейн данных и торговой аналитики
- Интеграция с индексированными блокчейн данными The Graph

## Переменные окружения

### Обязательные
- `THEGRAPH_API_KEY` - API ключ для доступа к сервисам The Graph

## Примеры использования

```
Show me the schema for subgraph QmZBQcF... in a readable format
```

```
Find the top 5 tokens by trading volume in the last 24 hours from subgraph QmZBQcF...
```

```
Show me all pairs with liquidity greater than 1 million USD in subgraph QmZBQcF...
```

```
Analyze the trading volume of USDT pairs in the last week using subgraph QmZBQcF...
```

```
Find unusual trading patterns in the last 24 hours from subgraph QmZBQcF...
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/thegraph-mcp)

## Примечания

Требует Python 3.10+ и лицензируется под MIT License. Поддерживает запросы на естественном языке для анализа блокчейн данных и торговой аналитики.