---
title: OpenLink Generic SQLAlchemy Object-Relational Database Connectivity for PyODBC MCP сервер
description: Легковесный MCP сервер, который обеспечивает подключение к базам данных ODBC через SQLAlchemy и pyodbc, совместимый с Virtuoso DBMS и другими бэкендами баз данных с провайдерами SQLAlchemy.
tags:
- Database
- Analytics
- Integration
- API
author: OpenLinkSoftware
featured: false
---

Легковесный MCP сервер, который обеспечивает подключение к базам данных ODBC через SQLAlchemy и pyodbc, совместимый с Virtuoso DBMS и другими бэкендами баз данных с провайдерами SQLAlchemy.

## Установка

### Из исходников

```bash
git clone https://github.com/OpenLinkSoftware/mcp-sqlalchemy-server.git
cd mcp-sqlalchemy-server
```

### Предварительные требования

```bash
pip install uv
# или
brew install uv
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "my_database": {
      "command": "uv",
      "args": ["--directory", "/path/to/mcp-sqlalchemy-server", "run", "mcp-sqlalchemy-server"],
      "env": {
        "ODBC_DSN": "dsn_name",
        "ODBC_USER": "username",
        "ODBC_PASSWORD": "password",
        "API_KEY": "sk-xxx"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `podbc_get_schemas` | Получить список схем баз данных, доступных для подключенной системы управления базами данных (DBMS) |
| `podbc_get_tables` | Получить список таблиц, связанных с выбранной схемой базы данных |
| `podbc_describe_table` | Предоставить описание таблицы, включая названия столбцов, типы данных, обработку NULL, автоинкремент... |
| `podbc_filter_table_names` | Получить список таблиц по шаблону подстроки, связанных с выбранной схемой базы данных |
| `podbc_query_database` | Выполнить SQL запрос и вернуть результаты в формате JSONL |
| `podbc_execute_query` | Выполнить SQL запрос и вернуть результаты в формате JSONL |
| `podbc_execute_query_md` | Выполнить SQL запрос и вернуть результаты в формате таблицы Markdown |
| `podbc_spasql_query` | Выполнить SPASQL запрос и вернуть результаты |
| `podbc_sparql_query` | Выполнить SPARQL запрос и вернуть результаты |
| `podbc_virtuoso_support_ai` | Взаимодействие с помощником/агентом поддержки Virtuoso -- специфичная для Virtuoso функция взаимодействия... |

## Возможности

- Получение схем: получение и отображение всех названий схем из подключенной базы данных
- Получение таблиц: извлечение информации о таблицах для конкретных схем или всех схем
- Описание таблицы: генерация детального описания структур таблиц с названиями столбцов, типами данных, атрибутами nullable, первичными и внешними ключами
- Поиск таблиц: фильтрация и извлечение таблиц на основе подстрок названий
- Выполнение хранимых процедур: в случае Virtuoso, выполнение хранимых процедур и получение результатов
- Выполнение запросов: формат результатов JSONL, оптимизированный для структурированных ответов
- Выполнение запросов: формат таблицы Markdown, идеальный для отчетности и визуализации
- Поддержка множественных систем баз данных: Virtuoso, PostgreSQL, MySQL, SQLite
- Поддержка SPARQL и SPASQL запросов для Virtuoso
- Интеграция с помощником AI поддержки Virtuoso

## Переменные окружения

### Обязательные
- `ODBC_DSN` - название источника данных ODBC
- `ODBC_USER` - имя пользователя базы данных
- `ODBC_PASSWORD` - пароль базы данных

### Опциональные
- `API_KEY` - ключ API для AI сервисов

## Ресурсы

- [GitHub Repository](https://github.com/OpenLinkSoftware/mcp-sqlalchemy-server)

## Примечания

Требует настройки ODBC DSN в ~/.odbc.ini и среды выполнения unixODBC. Поддерживает множественные форматы подключения к базам данных, включая virtuoso+pyodbc://user:password@ODBC_DSN, postgresql://, mysql+pymysql://, и sqlite:///. Для устранения неполадок установите MCP Inspector командой 'npm install -g @modelcontextprotocol/inspector'.