---
title: Vertica MCP сервер
description: Vertica MCP сервер, который обеспечивает управление подключениями к базе данных, операции запросов и инспекцию схем с настраиваемыми правами безопасности и поддержкой SSL.
tags:
- Database
- Analytics
- Security
- API
author: Community
featured: false
install_command: npx -y @smithery/cli install @nolleh/mcp-vertica --client claude
---

Vertica MCP сервер, который обеспечивает управление подключениями к базе данных, операции запросов и инспекцию схем с настраиваемыми правами безопасности и поддержкой SSL.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @nolleh/mcp-vertica --client claude
```

### UVX

```bash
uvx mcp-vertica
```

### Docker

```bash
docker run -i --rm nolleh/mcp-vertica
```

## Конфигурация

### UVX с переменными окружения

```json
{
  "mcpServers": {
    "vertica": {
      "command": "uvx",
      "args": ["mcp-vertica"],
      "env": {
        "VERTICA_HOST": "localhost",
        "VERTICA_PORT": 5433,
        "VERTICA_DATABASE": "VMart",
        "VERTICA_USER": "dbadmin",
        "VERTICA_PASSWORD": "test_password",
        "VERTICA_CONNECTION_LIMIT": 10,
        "VERTICA_SSL": false,
        "VERTICA_SSL_REJECT_UNAUTHORIZED": true
      }
    }
  }
}
```

### UVX с аргументами

```json
{
  "mcpServers": {
    "vertica": {
      "command": "uvx",
      "args": [
        "mcp-vertica",
        "--host=localhost",
        "--db-port=5433",
        "--database=VMart",
        "--user=dbadmin",
        "--password=test_password",
        "--connection-limit=10"
      ]
    }
  }
}
```

### Docker

```json
{
  "mcpServers": {
    "vertica": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "nolleh/mcp-vertica"],
      "env": {
        "VERTICA_HOST": "localhost",
        "VERTICA_PORT": 5433,
        "VERTICA_DATABASE": "VMart",
        "VERTICA_USER": "dbadmin",
        "VERTICA_PASSWORD": "test_password",
        "VERTICA_CONNECTION_LIMIT": 10,
        "VERTICA_SSL": false,
        "VERTICA_SSL_REJECT_UNAUTHORIZED": true
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `execute_query` | Выполнение SQL запросов с поддержкой всех SQL операций |
| `stream_query` | Потоковая передача больших результатов запросов партиями с настраиваемым размером партии |
| `copy_data` | Массовая загрузка данных с использованием команды COPY, эффективно для больших наборов данных |
| `get_table_structure` | Получение детальной структуры таблицы, включая информацию о колонках и ограничениях |
| `list_indexes` | Список всех индексов для таблицы с типом индекса, уникальностью и информацией о колонках |
| `list_views` | Список всех представлений в схеме с определениями представлений |

## Возможности

- Пулинг соединений с настраиваемыми лимитами
- Поддержка SSL/TLS с валидацией сертификатов
- Автоматическая очистка соединений и обработка таймаутов
- Потоковая передача больших результатов запросов партиями
- Массовые операции с данными с помощью команды COPY
- Управление транзакциями
- Инспекция структуры таблиц и схем
- Управление индексами и представлениями
- Права доступа на уровне операций (INSERT, UPDATE, DELETE, DDL)
- Права доступа специфичные для схем

## Переменные окружения

### Обязательные
- `VERTICA_HOST` - Хост базы данных Vertica
- `VERTICA_PORT` - Порт базы данных Vertica
- `VERTICA_DATABASE` - Имя базы данных Vertica
- `VERTICA_USER` - Имя пользователя базы данных
- `VERTICA_PASSWORD` - Пароль базы данных

### Опциональные
- `VERTICA_CONNECTION_LIMIT` - Максимальное количество соединений с базой данных
- `VERTICA_SSL` - Включить SSL/TLS соединение
- `VERTICA_SSL_REJECT_UNAUTHORIZED` - Отклонять неавторизованные SSL сертификаты
- `ALLOW_INSERT_OPERATION` - Разрешить INSERT операции
- `ALLOW_UPDATE_OPERATION` - Разрешить UPDATE операции
- `ALLOW_DELETE_OPERATION` - Разрешить DELETE операции
- `ALLOW_DDL_OPERATION` - Разрешить DDL операции
- `SCHEMA_INSERT_PERMISSIONS` - Права INSERT специфичные для схемы (формат: schema1:true,schema2:false)

## Ресурсы

- [GitHub Repository](https://github.com/nolleh/mcp-vertica)

## Примечания

Первая реализация Vertica MCP сервера. Включен в официальный реестр Model Context Protocol. Поддерживает булевые флаги путем добавления их в массив args или их опущения для отключения. Для пустых паролей используйте пустую строку. Режим отладки доступен при запуске с Docker.