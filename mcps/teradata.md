---
title: Teradata MCP сервер
description: MCP сервер, который обеспечивает безопасное взаимодействие с базой данных
  и возможности бизнес-аналитики через Teradata с корпоративной OAuth
  2.1 аутентификацией.
tags:
- Database
- Analytics
- Security
- API
- Integration
author: arturborycki
featured: false
---

MCP сервер, который обеспечивает безопасное взаимодействие с базой данных и возможности бизнес-аналитики через Teradata с корпоративной OAuth 2.1 аутентификацией.

## Установка

### Из исходников

```bash
git clone https://github.com/arturborycki/mcp-teradata.git
cd mcp-teradata
uv install
uv run teradata-mcp "teradatasql://user:password@host/database"
```

### Docker

```bash
docker-compose up -d
```

### Docker с OAuth

```bash
docker-compose -f docker-compose.oauth.yml up -d
```

### Сборка

```bash
uv build
```

## Конфигурация

### Базовая конфигурация Claude Desktop

```json
{
  "mcpServers": {
    "teradata": {
      "command": "uv",
      "args": [
        "--directory",
        "/Users/MCP/mcp-teradata",
        "run",
        "teradata-mcp"
      ],
      "env": {
        "DATABASE_URI": "teradatasql://user:passwd@host/database"
      }
    }
  }
}
```

### Claude Desktop с OAuth

```json
{
  "mcpServers": {
    "teradata": {
      "command": "uv", 
      "args": [
        "--directory",
        "/Users/MCP/mcp-teradata",
        "run",
        "teradata-mcp"
      ],
      "env": {
        "DATABASE_URI": "teradatasql://user:passwd@host/database",
        "OAUTH_ENABLED": "true",
        "KEYCLOAK_URL": "https://your-keycloak.com",
        "KEYCLOAK_REALM": "teradata-realm",
        "KEYCLOAK_CLIENT_ID": "teradata-mcp",
        "KEYCLOAK_CLIENT_SECRET": "your-secret",
        "OAUTH_RESOURCE_SERVER_URL": "https://your-server.com"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `query` | Выполняет SELECT запросы для чтения данных из базы данных |
| `list_db` | Выводит список всех баз данных в системе Teradata |
| `list_tables` | Выводит список объектов в базе данных |
| `show_tables_details` | Показывает подробную информацию о таблицах базы данных |
| `list_missing_values` | Выводит список топовых полей с отсутствующими значениями в таблице |
| `list_negative_values` | Показывает количество полей с отрицательными значениями в таблице |
| `list_distinct_values` | Выводит количество уникальных категорий для колонки в таблице |
| `standard_deviation` | Показывает среднее значение и стандартное отклонение для колонки в таблице |

## Возможности

- OAuth 2.1 аутентификация с интеграцией Keycloak
- JWT валидация токенов с использованием JWKS endpoints
- Авторизация на основе областей видимости для точного контроля доступа
- Метаданные защищенных ресурсов (совместимо с RFC 9728)
- Поддержка Token Introspection для непрозрачных токенов
- Готовая к продакшену устойчивость соединений и обработка ошибок
- Автоматический повтор подключений для повышения надежности
- Совместимость транспорта через SSE, Streamable HTTP и Stdio
- Discovery endpoints для OAuth защищенных ресурсов
- Health check endpoints со статусом OAuth

## Переменные окружения

### Обязательные
- `DATABASE_URI` - строка подключения к базе данных Teradata

### Опциональные
- `OAUTH_ENABLED` - включает OAuth аутентификацию
- `KEYCLOAK_URL` - URL сервера Keycloak
- `KEYCLOAK_REALM` - имя realm в Keycloak
- `KEYCLOAK_CLIENT_ID` - ID клиента Keycloak
- `KEYCLOAK_CLIENT_SECRET` - секрет клиента Keycloak
- `OAUTH_RESOURCE_SERVER_URL` - URL идентификации сервера ресурсов
- `TOOL_RETRY_MAX_ATTEMPTS` - количество попыток повтора подключения к базе данных
- `TOOL_RETRY_DELAY_SECONDS` - задержка между попытками повтора в секундах

## Ресурсы

- [GitHub Repository](https://github.com/arturborycki/mcp-teradata)

## Примечания

Поддерживает OAuth области видимости: teradata:read, teradata:write, teradata:query, teradata:admin, teradata:schema. Включает автоматизированный скрипт настройки Keycloak и комплексные инструменты тестирования OAuth. Предоставляет discovery endpoints для метаданных защищенных ресурсов и возможностей сервера.