---
title: dune-analytics-mcp MCP сервер
description: MCP сервер, который соединяет данные Dune Analytics с AI агентами, обеспечивая легкий доступ к аналитике блокчейна и криптовалют через запросы Dune.
tags:
- Analytics
- API
- Finance
- Database
- Integration
author: kukapay
featured: false
install_command: mcp install main.py --name "Dune Analytics"
---

MCP сервер, который соединяет данные Dune Analytics с AI агентами, обеспечивая легкий доступ к аналитике блокчейна и криптовалют через запросы Dune.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @kukapay/dune-analytics-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/kukapay/dune-analytics-mcp.git
cd dune-analytics-mcp
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_latest_result` | Получить последние результаты запроса Dune по ID |
| `run_query` | Выполнить запрос Dune по ID и получить результаты |

## Возможности

- Получение последних результатов запроса Dune по ID
- Выполнение запроса Dune по ID и получение результатов
- Все результаты возвращаются в формате CSV для удобной обработки

## Переменные окружения

### Обязательные
- `DUNE_API_KEY` - Действующий API ключ Dune Analytics из настроек Dune Analytics

## Примеры использования

```
Get latest results for dune query 1215383
```

```
Run dune query 1215383
```

```
get_latest_result(query_id=4853921)
```

```
run_query(query_id=1215383)
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/dune-analytics-mcp)

## Примечания

Требует Python 3.10+. Доступен режим разработки с 'mcp dev main.py' для горячей перезагрузки. ID запросов - это целые числа, ссылающиеся на конкретные запросы Dune Analytics.