---
title: CIViC MCP сервер
description: MCP сервер для работы с базой данных CIViC (Clinical Interpretation of Variants in Cancer), позволяющий выполнять структурированные запросы и анализ информации о геномике рака и клинических интерпретациях вариантов через GraphQL и SQL.
tags:
- Database
- API
- Analytics
- Search
author: QuentinCody
featured: false
---

MCP сервер для работы с базой данных CIViC (Clinical Interpretation of Variants in Cancer), позволяющий выполнять структурированные запросы и анализ информации о геномике рака и клинических интерпретациях вариантов через GraphQL и SQL.

## Установка

### Деплой в Cloudflare Workers

```bash
git clone <repository-url>
cd civic-mcp-server
npm install
npm run deploy
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "civic-mcp-server": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://civic-mcp-server.quentincody.workers.dev/sse"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `civic_graphql_query` | Выполнение GraphQL запросов к CIViC API |
| `civic_query_sql` | Запросы к подготовленным данным с помощью SQL |

## Возможности

- Конвертация GraphQL в SQL: Автоматически преобразует ответы CIViC API в структурированные таблицы SQLite
- Эффективное хранение данных: Использует Cloudflare Durable Objects с SQLite для промежуточного хранения и запросов
- Умная обработка ответов: Оптимизирует производительность, обходя промежуточное хранение для небольших ответов, ошибок и запросов схемы
- Двухэтапный пайплайн: GraphQL запросы и SQL-анализ промежуточных данных
- Управление датасетами: Вспомогательные эндпоинты для управления промежуточными датасетами
- Три MCP промпта: get-variant-evidence, get-variant-assertions, get-variant-data с надежной генерацией GraphQL

## Примеры использования

```
Какие последние данные по мутациям BRAF?
```

```
Покажи все терапевтические интерпретации для вариантов рака легких
```

```
Найди гены с наибольшим количеством данных в базе CIViC
```

```
/get-variant-evidence molecularProfileName:"TP53 Mutation" diseaseName:"Lung Adenocarcinoma" evidenceType:"PROGNOSTIC" first:"200"
```

```
/get-variant-assertions molecularProfileName:"TPM3-NTRK1 Fusion" therapyName:"Larotrectinib" status:"ALL"
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/civic-mcp-server)

## Примечания

Реализует спецификацию MCP 2025-06-18. Требует деплоя в Cloudflare Workers и предоставляет эндпоинты управления датасетами по адресу /datasets. Использует интеллектуальную обработку ответов для оптимизации использования контекста, сохраняя большие результаты в SQLite и возвращая небольшие ответы напрямую.