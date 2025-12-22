---
title: PostgreSQL MCP сервер
description: PostgreSQL MCP сервер, который предоставляет HTTP и Stdio транспорты для инспекции схемы базы данных и выполнения read-only запросов с управлением сессиями.
tags:
- Database
- API
- DevOps
- Integration
- Analytics
author: Community
featured: false
---

PostgreSQL MCP сервер, который предоставляет HTTP и Stdio транспорты для инспекции схемы базы данных и выполнения read-only запросов с управлением сессиями.

## Установка

### NPX

```bash
npx @ahmedmustahid/postgres-mcp-server
```

### NPX Stdio

```bash
npx @ahmedmustahid/postgres-mcp-server stdio
```

### Podman/Docker

```bash
cp .env.example .env
# Edit .env with your credentials
set -a
source .env
set +a
podman machine start
make podman-up
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "postgres-mcp-server": {
      "command": "npx",
      "args": [
        "@ahmedmustahid/postgres-mcp-server",
        "stdio"
      ],
      "env": {
        "POSTGRES_USERNAME": "your-username",
        "POSTGRES_PASSWORD": "your-password",
        "POSTGRES_HOST": "hostname",
        "POSTGRES_DATABASE": "database-name"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `query` | Выполнение read-only SQL запросов к базе данных |

## Возможности

- Поддержка двух транспортов: HTTP (StreamableHTTPServerTransport) и Stdio (StdioServerTransport)
- Ресурсы базы данных: Список таблиц и получение информации о схеме
- Инструмент запросов: Выполнение read-only SQL запросов
- Сессии с состоянием: HTTP транспорт поддерживает управление сессиями
- Поддержка Docker: Контейнеризированные деплои для обоих транспортов
- Готов к продакшену: Корректное завершение работы, обработка ошибок и логирование

## Переменные окружения

### Обязательные
- `POSTGRES_USERNAME` - имя пользователя PostgreSQL
- `POSTGRES_PASSWORD` - пароль PostgreSQL
- `POSTGRES_HOST` - хост PostgreSQL
- `POSTGRES_DATABASE` - имя базы данных PostgreSQL

### Опциональные
- `POSTGRES_URL` - строка подключения к базе данных PostgreSQL
- `POSTGRES_PORT` - порт PostgreSQL
- `PORT` - порт HTTP сервера
- `HOST` - хост HTTP сервера
- `CORS_ORIGIN` - разрешенные CORS источники (через запятую)
- `NODE_ENV` - режим окружения

## Примеры использования

```
Show `sales` table from last year
```

## Ресурсы

- [GitHub Repository](https://github.com/ahmedmustahid/postgres-mcp-server)

## Примечания

Поддерживает HTTP и Stdio транспорты с различными возможностями. HTTP транспорт предоставляет сессии с состоянием и одновременные подключения, в то время как Stdio используется для прямого CLI использования. Включает health check эндпоинт по адресу `/health` и поддерживает MCP Inspector для тестирования.