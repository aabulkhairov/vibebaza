---
title: MariaDB MCP сервер
description: Реализация MCP сервера для получения данных из баз данных MariaDB с поддержкой операций только для чтения.
tags:
- Database
- Integration
- Analytics
- Storage
author: Community
featured: false
---

Реализация MCP сервера для получения данных из баз данных MariaDB с поддержкой операций только для чтения.

## Установка

### Опубликованный сервер (uvx)

```bash
uvx mcp-server-mariadb --host ${DB_HOST} --port ${DB_PORT} --user ${DB_USER} --password ${DB_PASSWORD} --database ${DB_NAME}
```

### Разработка (uv)

```bash
uv --directory /YOUR/SOURCE/PATH/mcp-server-mariadb/src/mcp_server_mariadb run server.py
```

### Установка MariaDB Connector (Mac)

```bash
brew install mariadb-connector-c
echo 'export PATH="/opt/homebrew/opt/mariadb-connector-c/bin:$PATH"' >> ~/.bashrc
export MARIADB_CONFIG=$(brew --prefix mariadb-connector-c)/bin/mariadb_config
uv add mariadb
```

## Конфигурация

### Claude Desktop (опубликованная версия)

```json
{
    "mcpServers": {
        "mcp_server_mariadb": {
            "command": "/PATH/TO/uvx"
            "args": [
                "mcp-server-mariadb",
                "--host",
                "${DB_HOST}",
                "--port",
                "${DB_PORT}",
                "--user",
                "${DB_USER}",
                "--password",
                "${DB_PASSWORD}",
                "--database",
                "${DB_NAME}"
            ]
        }
    }
}
```

### Claude Desktop (разработка)

```json
{
    "mcpServers": {
        "mcp_server_mariadb": {
            "command": "/PATH/TO/uv",
            "args": [
                "--directory",
                "/YOUR/SOURCE/PATH/mcp-server-mariadb/src/mcp_server_mariadb",
                "run",
                "server.py"
            ],
            "env": {
                "MARIADB_HOST": "127.0.0.1",
                "MARIADB_USER": "USER",
                "MARIADB_PASSWORD": "PASSWORD",
                "MARIADB_DATABASE": "DATABASE",
                "MARIADB_PORT": "3306"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `query_database` | Выполнение операций только для чтения в MariaDB |

## Возможности

- Отображение списка схем в базе данных
- Выполнение операций только для чтения в MariaDB
- Кроссплатформенная поддержка (MacOS и Windows)

## Переменные окружения

### Обязательные
- `MARIADB_HOST` - имя хоста сервера MariaDB
- `MARIADB_USER` - имя пользователя MariaDB
- `MARIADB_PASSWORD` - пароль MariaDB
- `MARIADB_DATABASE` - имя базы данных MariaDB
- `MARIADB_PORT` - порт сервера MariaDB

### Опциональные
- `MARIADB_CONFIG` - путь к утилите mariadb_config

## Ресурсы

- [GitHub Repository](https://github.com/abel9851/mcp-server-mariadb)

## Примечания

Лицензирован под лицензией MIT. На Mac может потребоваться установка mariadb-connector-c для решения проблем с зависимостью mariadb_config. Пути к файлам конфигурации: MacOS: ~/Library/Application Support/Claude/claude_desktop_config.json, Windows: %APPDATA%\Claude\claude_desktop_config.json