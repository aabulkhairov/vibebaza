---
title: CockroachDB MCP сервер
description: MCP сервер, который предоставляет интерфейс на естественном языке для AI агентов и LLM для управления, мониторинга и запросов к базам данных CockroachDB через комплексные операции с базами данных и мониторинг кластера.
tags:
- Database
- Monitoring
- Analytics
- AI
- DevOps
author: Community
featured: false
install_command: npx -y @smithery/cli install @amineelkouhen/mcp-cockroachdb
---

MCP сервер, который предоставляет интерфейс на естественном языке для AI агентов и LLM для управления, мониторинга и запросов к базам данных CockroachDB через комплексные операции с базами данных и мониторинг кластера.

## Установка

### uvx

```bash
uvx --from git+https://github.com/amineelkouhen/mcp-cockroachdb.git@0.1.0 cockroachdb-mcp-server --url postgresql://localhost:26257/defaultdb
```

### Разработка

```bash
git clone https://github.com/amineelkouhen/mcp-cockroachdb.git
cd mcp-cockroachdb
uv venv
source .venv/bin/activate
uv sync
uv run cockroachdb-mcp-server --help
```

### Docker

```bash
docker build -t mcp-cockroachdb .
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "cockroach-mcp-server": {
            "type": "stdio",
            "command": "/opt/homebrew/bin/uvx",
            "args": [
                "--from", "git+https://github.com/amineelkouhen/mcp-cockroachdb.git",
                "cockroachdb-mcp-server",
                "--url", "postgresql://localhost:26257/defaultdb"
            ]
        }
    }
}
```

### Claude Desktop (Переменные окружения)

```json
{
    "mcpServers": {
        "cockroach": {
            "command": "<full_path_uv_command>",
            "args": [
                "--directory",
                "<your_mcp_server_directory>",
                "run",
                "src/main.py"
            ],
            "env": {
                "CRDB_HOST": "<your_cockroachdb_hostname>",
                "CRDB_PORT": "<your_cockroachdb_port>",
                "CRDB_DATABASE": "<your_cockroach_database>",
                "CRDB_USERNAME": "<your_cockroachdb_user>",
                "CRDB_PWD": "<your_cockroachdb_password>",
                "CRDB_SSL_MODE": "disable|allow|prefer|require|verify-ca|verify-full"
            }
        }
    }
}
```

### Docker

```json
{
  "mcpServers": {
    "cockroach": {
      "command": "docker",
      "args": ["run",
                "--rm",
                "--name",
                "cockroachdb-mcp-server",
                "-e", "CRDB_HOST=<cockroachdb_host>",
                "-e", "CRDB_PORT=<cockroachdb_port>",
                "-e", "CRDB_DATABASE=<cockroachdb_database>",
                "-e", "CRDB_USERNAME=<cockroachdb_user>",
                "mcp-cockroachdb"]
    }
  }
}
```

### Augment

```json
{
  "mcpServers": {
    "CockroachDB MCP Server": {
      "command": "uvx",
      "args": [
        "--from",
        "git+https://github.com/cockroachdb/mcp-cockroachdb.git",
        "cockroachdb-mcp-server",
        "--url",
        "postgresql://root@localhost:26257/defaultdb"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `cluster_health` | Получение здоровья кластера и статуса узлов |
| `running_queries` | Показать текущие выполняющиеся запросы |
| `query_performance` | Анализ статистики производительности запросов |
| `replication_status` | Получение статуса репликации и распределения для таблиц или базы данных |
| `connect_database` | Подключение к базе данных CockroachDB |
| `list_databases` | Список доступных баз данных |
| `create_database` | Создание новых баз данных |
| `drop_database` | Удаление баз данных |
| `switch_database` | Переключение между базами данных |
| `connection_status` | Получение статуса подключения и активных сессий |
| `database_settings` | Получение настроек базы данных |
| `create_table` | Создание таблиц и представлений |
| `drop_table` | Удаление таблиц и представлений |
| `describe_table` | Описание структуры таблицы |
| `bulk_import` | Массовый импорт данных в таблицы |

## Возможности

- Запросы на естественном языке: Позволяет AI агентам выполнять запросы и создавать транзакции используя естественный язык
- Поиск и фильтрация: Поддерживает эффективное извлечение данных и поиск в CockroachDB
- Мониторинг кластера: Проверка и мониторинг статуса кластера CockroachDB, включая здоровье узлов и репликацию
- Операции с базами данных: Выполнение всех операций связанных с базами данных, таких как создание, удаление и конфигурация
- Управление таблицами: Обработка таблиц, индексов и схем для гибкого моделирования данных
- Беспроблемная интеграция MCP: Работает с любым MCP клиентом для плавной коммуникации
- Масштабируемый и легковесный: Разработан для высокопроизводительных операций с данными

## Переменные окружения

### Опциональные
- `CRDB_HOST` - Имя хоста или адрес узла CockroachDB или балансировщика нагрузки
- `CRDB_PORT` - Номер порта SQL интерфейса узла CockroachDB или балансировщика нагрузки
- `CRDB_DATABASE` - Имя базы данных для использования в качестве текущей базы данных
- `CRDB_USERNAME` - SQL пользователь, который будет владеть клиентской сессией
- `CRDB_PWD` - Пароль пользователя
- `CRDB_SSL_MODE` - Какой тип безопасного соединения использовать
- `CRDB_SSL_CA_PATH` - Путь к CA сертификату, когда sslmode не disable
- `CRDB_SSL_CERTFILE` - Путь к клиентскому сертификату, когда sslmode не disable

## Ресурсы

- [GitHub Repository](https://github.com/amineelkouhen/mcp-cockroachdb)

## Примечания

Поддерживает stdio транспорт с streamable-http транспортом в будущих релизах. Интегрируется с OpenAI Agents SDK, Claude Desktop, VS Code с GitHub Copilot, Cursor и Augment. Доступен как официальный Docker образ по адресу mcp/cockroachdb.