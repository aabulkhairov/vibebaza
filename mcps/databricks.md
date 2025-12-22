---
title: Databricks MCP сервер
description: Сервер Model Context Protocol, который подключается к Databricks API, позволяя LLM выполнять SQL запросы к SQL хранилищам, получать списки задач и их статусы.
tags:
- Database
- Analytics
- Cloud
- API
author: JordiNeil
featured: false
---

Сервер Model Context Protocol, который подключается к Databricks API, позволяя LLM выполнять SQL запросы к SQL хранилищам, получать списки задач и их статусы.

## Установка

### Из исходного кода

```bash
git clone repository
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Запуск сервера

```bash
python main.py
```

### Тестирование с Inspector

```bash
npx @modelcontextprotocol/inspector python3 main.py
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `run_sql_query` | Выполняет SQL запросы к вашему Databricks SQL хранилищу |
| `list_jobs` | Показывает все задачи Databricks в вашей рабочей области |
| `get_job_status` | Получает статус конкретной задачи Databricks по ID |
| `get_job_details` | Получает подробную информацию о конкретной задаче Databricks |

## Возможности

- Выполнение SQL запросов к Databricks SQL хранилищам
- Просмотр всех задач Databricks
- Получение статуса конкретных задач Databricks
- Получение подробной информации о задачах Databricks

## Переменные окружения

### Обязательные
- `DATABRICKS_HOST` - URL вашего экземпляра Databricks
- `DATABRICKS_TOKEN` - Ваш персональный токен доступа для аутентификации
- `DATABRICKS_HTTP_PATH` - Путь к конечной точке SQL хранилища

## Примеры использования

```
Show me all tables in the database
```

```
Run a query to count records in the customer table
```

```
List all my Databricks jobs
```

```
Check the status of job #123
```

```
Show me details about job #456
```

## Ресурсы

- [GitHub Repository](https://github.com/JordiNeil/mcp-databricks-server)

## Примечания

Требует Python 3.7+, рабочую область Databricks с персональным токеном доступа, конечную точку SQL хранилища и соответствующие разрешения. Включает скрипт тестирования соединения для проверки. При использовании важно защищать токены доступа и запускать в безопасном окружении.