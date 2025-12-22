---
title: Open Targets MCP сервер
description: MCP сервер, предоставляющий доступ к Open Targets Platform API для запросов ассоциаций мишеней и заболеваний, данных по открытию лекарств и биомедицинской исследовательской информации через GraphQL.
tags:
- Database
- API
- Analytics
- Search
author: QuentinCody
featured: false
---

MCP сервер, предоставляющий доступ к Open Targets Platform API для запросов ассоциаций мишеней и заболеваний, данных по открытию лекарств и биомедицинской исследовательской информации через GraphQL.

## Установка

### NPX с mcp-remote

```bash
npx mcp-remote https://open-targets-mcp-server.quentincody.workers.dev/mcp
```

## Конфигурация

### Claude Desktop (Рекомендуется)

```json
"open-targets-worker": {
  "command": "npx",
  "args": [
    "mcp-remote",
    "https://open-targets-mcp-server.quentincody.workers.dev/mcp"
  ]
}
```

### Claude Desktop (Legacy SSE)

```json
"open-targets-worker": {
  "command": "npx",
  "args": [
    "mcp-remote",
    "https://open-targets-mcp-server.quentincody.workers.dev/sse"
  ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `opentargets_graphql_query` | Выполнение GraphQL запросов к Open Targets Platform API с опциональными переменными |

## Возможности

- Доступ к Open Targets Platform API через GraphQL запросы
- Информация о биологических мишенях, идентифицируемых по Ensembl ID
- Данные о заболеваниях и фенотипах, идентифицируемые по EFO ID
- Данные о лекарствах и химических соединениях, идентифицируемые по ChEMBL ID
- Возможности интроспекции схемы для изучения доступных типов данных
- Поддержка параметризованных запросов с переменными
- Два транспортных протокола: Streamable HTTP (рекомендуется) и SSE (legacy)

## Примеры использования

```
Получить детали для конкретной генной мишени используя Ensembl ID ENSG00000169083
```

```
Список всех доступных типов данных в схеме Open Targets
```

```
Запросить информацию об астме используя EFO ID EFO_0000270
```

```
Получить информацию о лекарстве используя ChEMBL ID CHEMBL1201236
```

```
Изучить данные о трактабельности мишеней и генетических ограничениях
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/open-targets-mcp-server)

## Примечания

Лицензировано под MIT License с требованием академического цитирования. Для крупномасштабного получения данных Open Targets рекомендует использовать их официальные загрузки данных или инстанс Google BigQuery вместо повторных GraphQL запросов. См. GRAPHQL_EXAMPLES.md для правильных примеров запросов и избежания распространенных ошибок.