---
title: OpenLink Generic Python Open Database Connectivity MCP сервер
description: Легковесный MCP сервер, который обеспечивает доступ к базам данных через ODBC с помощью PyODBC,
  совместимый с Virtuoso DBMS и любыми СУБД с ODBC драйверами.
tags:
- Database
- Analytics
- Integration
- API
author: OpenLinkSoftware
featured: false
---

Легковесный MCP сервер, который обеспечивает доступ к базам данных через ODBC с помощью PyODBC, совместимый с Virtuoso DBMS и любыми СУБД с ODBC драйверами.

## Установка

### Из исходного кода

```bash
git clone https://github.com/OpenLinkSoftware/mcp-pyodbc-server.git
cd mcp-pyodbc-server
```

### Предварительные требования - установка uv

```bash
pip install uv
```

### Предварительные требования - uv через Homebrew

```bash
brew install uv
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "my_database": {
      "command": "uv",
      "args": ["--directory", "/path/to/mcp-pyodbc-server", "run", "mcp-pyodbc-server"],
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

### Настройка ODBC DSN

```json
[VOS]
Description = OpenLink Virtuoso
Driver = /path/to/virtodbcu_r.so
Database = Demo
Address = localhost:1111
WideAsUTF16 = Yes
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `podbc_get_schemas` | Получить список схем базы данных, доступных для подключенной системы управления базами данных (СУБД) |
| `podbc_get_tables` | Получить список таблиц, связанных с выбранной схемой базы данных |
| `podbc_describe_table` | Предоставить описание таблицы, включая названия столбцов, типы данных, обработку null, автоинкремент... |
| `podbc_filter_table_names` | Получить список таблиц на основе шаблона подстроки из поля q, связанных с выбранной базой данных... |
| `podbc_query_database` | Выполнить SQL запрос и вернуть результаты в формате JSON |
| `podbc_execute_query` | Выполнить SQL запрос и вернуть результаты в формате JSONL |
| `podbc_execute_query_md` | Выполнить SQL запрос и вернуть результаты в формате таблицы Markdown |
| `podbc_spasql_query` | Выполнить SPASQL запрос и вернуть результаты (функция специфичная для Virtuoso) |
| `podbc_virtuoso_support_ai` | Взаимодействие с помощником/агентом поддержки Virtuoso для взаимодействия с LLM |

## Возможности

- Получение схем: Извлечение и вывод всех названий схем из подключенной базы данных
- Получение таблиц: Извлечение информации о таблицах для конкретных схем или всех схем
- Описание таблицы: Генерация детального описания структуры таблицы с информацией о столбцах, атрибутах nullable, первичных и внешних ключах
- Поиск таблиц: Фильтрация и извлечение таблиц на основе подстрок названий
- Выполнение хранимых процедур: Выполнение хранимых процедур при подключении к Virtuoso
- Выполнение запросов: Поддержка формата результатов JSONL и формата таблицы Markdown
- Поддержка SPASQL: Выполнение гибридных SQL/SPARQL запросов (специфично для Virtuoso)
- Интеграция с AI помощником: Возможности взаимодействия с LLM специфичные для Virtuoso

## Переменные окружения

### Обязательные
- `ODBC_DSN` - Имя источника данных ODBC для подключения к базе данных
- `ODBC_USER` - Имя пользователя базы данных для аутентификации
- `ODBC_PASSWORD` - Пароль базы данных для аутентификации

### Опциональные
- `API_KEY` - API ключ для интеграции с AI сервисами

## Ресурсы

- [GitHub Repository](https://github.com/OpenLinkSoftware/mcp-pyodbc-server)

## Примечания

Требуется настройка и конфигурация ODBC драйвера. Совместим с Virtuoso DBMS и любыми СУБД с ODBC драйверами. Включает MCP Inspector для устранения неполадок: `npm install -g @modelcontextprotocol/inspector` и запуск с `npx @modelcontextprotocol/inspector uv --directory /path/to/mcp-pyodbc-server run mcp-pyodbc-server`