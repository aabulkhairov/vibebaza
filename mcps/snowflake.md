---
title: Snowflake MCP сервер
description: MCP сервер, который обеспечивает взаимодействие с базой данных Snowflake, позволяя выполнять SQL-запросы и предоставляя аналитические данные и контекст схемы как ресурсы.
tags:
- Database
- Analytics
- Cloud
- Integration
- Productivity
author: Community
featured: false
---

MCP сервер, который обеспечивает взаимодействие с базой данных Snowflake, позволяя выполнять SQL-запросы и предоставляя аналитические данные и контекст схемы как ресурсы.

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp_snowflake_server --client claude
```

### UVX

```bash
uvx --python=3.12 mcp_snowflake_server --account your_account --warehouse your_warehouse --user your_user --password your_password --role your_role --database your_database --schema your_schema
```

### Из исходников

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv --directory /absolute/path/to/mcp_snowflake_server run mcp_snowflake_server
```

## Конфигурация

### Claude Desktop - Традиционная конфигурация

```json
"mcpServers": {
  "snowflake_pip": {
    "command": "uvx",
    "args": [
      "--python=3.12",
      "mcp_snowflake_server",
      "--account", "your_account",
      "--warehouse", "your_warehouse",
      "--user", "your_user",
      "--password", "your_password",
      "--role", "your_role",
      "--database", "your_database",
      "--schema", "your_schema"
    ]
  }
}
```

### Claude Desktop - TOML конфигурация

```json
"mcpServers": {
  "snowflake_production": {
    "command": "uvx",
    "args": [
      "--python=3.12",
      "mcp_snowflake_server",
      "--connections-file", "/path/to/snowflake_connections.toml",
      "--connection-name", "production"
    ]
  }
}
```

### Claude Desktop - Локальная установка

```json
"mcpServers": {
  "snowflake_local": {
    "command": "/absolute/path/to/uv",
    "args": [
      "--python=3.12",
      "--directory", "/absolute/path/to/mcp_snowflake_server",
      "run", "mcp_snowflake_server",
      "--connections-file", "/absolute/path/to/snowflake_connections.toml",
      "--connection-name", "development"
    ]
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `read_query` | Выполнение SELECT-запросов для чтения данных из базы |
| `write_query` | Выполнение INSERT, UPDATE или DELETE запросов (требует флаг --allow-write) |
| `create_table` | Создание новых таблиц в базе данных (требует флаг --allow-write) |
| `list_databases` | Список всех баз данных в инстансе Snowflake |
| `list_schemas` | Список всех схем в конкретной базе данных |
| `list_tables` | Список всех таблиц в конкретной базе данных и схеме |
| `describe_table` | Просмотр информации о колонках конкретной таблицы |
| `append_insight` | Добавление новых аналитических данных в ресурс заметок |

## Возможности

- Выполнение SQL-запросов для чтения и записи данных
- Просмотр схемы базы данных и метаданных
- Постоянно обновляемые заметки с аналитикой
- Сводки схем по каждой таблице как ресурсы
- Защита от записи с явным флагом --allow-write
- Поддержка множественных конфигураций соединений через TOML
- Возможности фильтрации для баз данных, схем и таблиц
- Поддержка аутентификации по приватному ключу и через внешний браузер

## Переменные окружения

### Обязательные
- `SNOWFLAKE_USER` - Имя пользователя Snowflake
- `SNOWFLAKE_ACCOUNT` - Идентификатор аккаунта Snowflake
- `SNOWFLAKE_ROLE` - Роль Snowflake для использования
- `SNOWFLAKE_DATABASE` - База данных по умолчанию для подключения
- `SNOWFLAKE_SCHEMA` - Схема по умолчанию для использования
- `SNOWFLAKE_WAREHOUSE` - Warehouse Snowflake для использования

### Опциональные
- `SNOWFLAKE_PASSWORD` - Пароль Snowflake
- `SNOWFLAKE_PRIVATE_KEY_PATH` - Путь к файлу приватного ключа для аутентификации
- `SNOWFLAKE_AUTHENTICATOR` - Метод аутентификации (например, externalbrowser)

## Ресурсы

- [GitHub Repository](https://github.com/isaacwasserman/mcp-snowflake-server)

## Примечания

По умолчанию операции записи отключены и должны быть явно разрешены флагом --allow-write. Сервер поддерживает фильтрацию конкретных баз данных, схем или таблиц через паттерны исключения. Контекстные ресурсы по каждой таблице доступны при включенной предзагрузке. Инструмент append_insight динамически обновляет ресурс memo://insights.