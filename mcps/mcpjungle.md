---
title: MCPJungle MCP сервер
description: Самохостинговый MCP Gateway, который служит централизованным реестром для всех серверов Model Context Protocol в организации, позволяя разработчикам управлять MCP серверами и предоставляя MCP клиентам возможность находить и использовать инструменты через единый шлюз.
tags:
- API
- Integration
- DevOps
- Security
- Analytics
author: mcpjungle
featured: true
---

Самохостинговый MCP Gateway, который служит централизованным реестром для всех серверов Model Context Protocol в организации, позволяя разработчикам управлять MCP серверами и предоставляя MCP клиентам возможность находить и использовать инструменты через единый шлюз.

## Установка

### Homebrew

```bash
brew install mcpjungle/mcpjungle/mcpjungle
```

### Docker Compose (Локально)

```bash
curl -O https://raw.githubusercontent.com/mcpjungle/MCPJungle/refs/heads/main/docker-compose.yaml
docker compose up -d
```

### Docker Compose (Продакшн)

```bash
curl -O https://raw.githubusercontent.com/mcpjungle/MCPJungle/refs/heads/main/docker-compose.prod.yaml
docker compose -f docker-compose.prod.yaml up -d
```

### Docker Pull

```bash
docker pull mcpjungle/mcpjungle
```

### Прямой бинарник

```bash
mcpjungle start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "mcpjungle": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "http://localhost:8080/mcp",
        "--allow-http"
      ]
    }
  }
}
```

### Регистрация Streamable HTTP сервера

```json
{
  "name": "<имя вашего mcp сервера>",
  "transport": "streamable_http",
  "description": "<описание>",
  "url": "<url mcp сервера>",
  "bearer_token": "<опциональный bearer токен для аутентификации>"
}
```

### Регистрация STDIO сервера

```json
{
  "name": "<имя вашего mcp сервера>",
  "transport": "stdio",
  "description": "<описание>",
  "command": "<команда для запуска mcp сервера, например 'npx', 'uvx'>",
  "args": ["аргументы", "для", "передачи", "команде"],
  "env": {
    "KEY": "значение"
  }
}
```

### Filesystem MCP сервер

```json
{
  "name": "filesystem",
  "transport": "stdio",
  "description": "filesystem mcp сервер",
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-filesystem", "."]
}
```

## Возможности

- Самохостинговый MCP Gateway для централизованного управления инструментами
- Поддержка протоколов транспорта STDIO и Streamable HTTP
- Реестр для управления несколькими MCP серверами из единого места
- Встроенная безопасность, приватность и контроль доступа для продакшн AI агентов
- Корпоративные функции включая мониторинг OpenTelemetry
- Возможность включения/отключения инструментов
- Система аутентификации
- Организация групп инструментов
- Поддержка баз данных PostgreSQL и SQLite
- Docker деплой с постоянным хранилищем

## Переменные окружения

### Опциональные
- `DATABASE_URL` - строка подключения к базе данных PostgreSQL
- `POSTGRES_HOST` - хост PostgreSQL (обязательно при использовании специфичных для postgres переменных окружения)
- `POSTGRES_PORT` - порт PostgreSQL
- `POSTGRES_USER` - имя пользователя PostgreSQL
- `POSTGRES_USER_FILE` - путь к файлу с именем пользователя PostgreSQL
- `POSTGRES_PASSWORD` - пароль PostgreSQL
- `POSTGRES_PASSWORD_FILE` - путь к файлу с паролем PostgreSQL
- `POSTGRES_DB` - имя базы данных PostgreSQL

## Примеры использования

```
Используйте context7 чтобы получить документацию для `/lodash/lodash`
```

```
mcpjungle register --name context7 --url https://mcp.context7.com/mcp
```

```
mcpjungle register --name calculator --description "Предоставляет базовые математические инструменты" --url http://127.0.0.1:8000/mcp
```

```
mcpjungle list tools
```

```
mcpjungle usage calculator__multiply
```

## Ресурсы

- [GitHub Repository](https://github.com/mcpjungle/MCPJungle)

## Примечания

MCPJungle использует каноническую схему именования для инструментов: <имя-mcp-сервера>__<имя-инструмента>. Сервер создаёт новые подключения для каждого вызова инструмента с STDIO серверами, что предотвращает сохранение состояния подключений, но избегает утечек памяти. Корпоративный режим включает дополнительные функции, такие как контроль доступа и мониторинг OpenTelemetry. При работе в Docker для доступа к файловой системе требуется правильная конфигурация монтирования томов.