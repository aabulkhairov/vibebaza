---
title: Databricks Genie MCP сервер
description: Model Context Protocol (MCP) сервер, который подключается к Databricks
  Genie API, позволяя LLM задавать вопросы на естественном языке, выполнять SQL запросы и
  взаимодействовать с разговорными агентами Databricks.
tags:
- Database
- Analytics
- AI
- Cloud
- API
author: yashshingvi
featured: false
---

Model Context Protocol (MCP) сервер, который подключается к Databricks Genie API, позволяя LLM задавать вопросы на естественном языке, выполнять SQL запросы и взаимодействовать с разговорными агентами Databricks.

## Установка

### Из исходников

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Установка MCP

```bash
mcp install main.py
```

### Docker

```bash
You can directly build and run docker to test the server
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_genie_space_id` | Получить список доступных ID и названий Genie пространств |
| `get_space_info` | Получить название и описание Genie пространства |
| `ask_genie` | Начать новый разговор с Genie и получить результаты |
| `follow_up` | Продолжить существующий разговор с Genie |

## Возможности

- Получение списка Genie пространств, доступных в вашем Databricks workspace (в настоящее время вручную/через ресурсы)
- Получение метаданных (название, описание) определенного Genie пространства
- Начало новых разговоров с Genie с помощью вопросов на естественном языке
- Задавание дополнительных вопросов в продолжающихся разговорах с Genie
- Получение SQL и таблиц результатов в структурированном формате

## Переменные окружения

### Обязательные
- `DATABRICKS_HOST` - URL вашего Databricks инстанса (например, your-databricks-instance.cloud.databricks.com) - Не добавляйте https
- `DATABRICKS_TOKEN` - Ваш персональный токен доступа для аутентификации в Databricks

## Ресурсы

- [GitHub Repository](https://github.com/yashshingvi/databricks-genie-MCP)

## Примечания

Требует Python 3.7+, Databricks workspace с персональным токеном доступа, включенный Genie API и разрешения на доступ к Genie пространствам. В настоящее время требует ручного добавления ID Genie пространств в функцию get_genie_space_id(), поскольку Databricks Genie API не предоставляет публичный эндпоинт для получения списка всех доступных ID пространств. Можно протестировать с помощью MCP инспектора командой 'npx @modelcontextprotocol/inspector python main.py'.