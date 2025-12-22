---
title: OpenLink Generic Open Database Connectivity MCP сервер
description: Универсальный ODBC сервер для Model Context Protocol, который предоставляет большим языковым моделям прозрачный доступ к источникам данных, доступным через ODBC, с помощью настроенных имен источников данных.
tags:
- Database
- Analytics
- Integration
- API
author: OpenLinkSoftware
featured: false
---

Универсальный ODBC сервер для Model Context Protocol, который предоставляет большим языковым моделям прозрачный доступ к источникам данных, доступным через ODBC, с помощью настроенных имен источников данных.

## Установка

### Из исходного кода

```bash
git clone https://github.com/OpenLinkSoftware/mcp-odbc-server.git
cd mcp-odbc-server
npm init -y
npm install @modelcontextprotocol/sdk zod tsx odbc dotenv
```

### Предварительные требования

```bash
nvm install v21.1.0
npm install @modelcontextprotocol/sdk zod tsx odbc dotenv
nvm alias default 21.1.0
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "ODBC": {
            "command": "/path/to/.nvm/versions/node/v21.1.0/bin/node",
            "args": [
                "/path/to/mcp-odbc-server/node_modules/.bin/tsx",
                "/path/to/mcp-odbc-server/src/main.ts"
            ],
            "env": {
                "ODBCINI": "/Library/ODBC/odbc.ini",
                "NODE_VERSION": "v21.1.0",
                "PATH": "~/.nvm/versions/node/v21.1.0/bin:${PATH}"
            },
            "disabled": false,
            "autoApprove": []
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_schemas` | Список схем базы данных, доступных для подключенной системы управления базами данных (СУБД) |
| `get_tables` | Список таблиц, связанных с выбранной схемой базы данных |
| `describe_table` | Предоставляет описание таблицы, связанной с указанной схемой базы данных, включая столбцы... |
| `filter_table_names` | Список таблиц, связанных с выбранной схемой базы данных, на основе шаблона подстроки из q... |
| `query_database` | Выполняет SQL-запрос и возвращает результаты в формате JSON Lines (JSONL) |
| `execute_query` | Выполняет SQL-запрос и возвращает результаты в формате JSON Lines (JSONL) |
| `execute_query_md` | Выполняет SQL-запрос и возвращает результаты в формате таблицы Markdown |
| `spasql_query` | Выполняет SPASQL-запрос и возвращает результаты |
| `sparql_query` | Выполняет SPARQL-запрос и возвращает результаты |
| `virtuoso_support_ai` | Взаимодействие с Virtuoso Support Assistant/Agent — специфическая функция Virtuoso для взаимодействия... |

## Возможности

- Универсальное ODBC-подключение к любому источнику данных, доступному через ODBC
- Возможности обнаружения схем и таблиц
- Множественные форматы результатов запросов (JSON, JSONL, Markdown)
- Поддержка SQL, SPASQL и SPARQL запросов
- Интеграция с AI-помощником, специфичным для Virtuoso
- Построен на TypeScript с основой node-odbc
- Совместим с любым ODBC драйвером/коннектором

## Переменные окружения

### Обязательные
- `ODBC_DSN` - Имя источника данных ODBC
- `ODBC_USER` - Имя пользователя базы данных
- `ODBC_PASSWORD` - Пароль базы данных
- `ODBCINI` - Путь к файлу ODBC INI

### Опциональные
- `API_KEY` - API ключ целевой большой языковой модели (LLM) для OpenLink AI Layer (OPAL) через ODBC

## Примеры использования

```
Execute the following query: SELECT TOP * from Demo..Customers
```

## Ресурсы

- [GitHub Repository](https://github.com/OpenLinkSoftware/mcp-odbc-server)

## Примечания

Требует Node.js версии 21.1.0 или выше. Включает специальное руководство по устранению проблем совместимости с Apple Silicon (ARM64). Поддерживает инструмент MCP Inspector для тестирования. Хотя примеры сосредоточены на Virtuoso ODBC Connector, он работает и с другими ODBC коннекторами.