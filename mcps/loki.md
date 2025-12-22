---
title: Loki MCP сервер
description: Go-based MCP сервер, который интегрируется с Grafana Loki для запроса данных логов с использованием LogQL, поддерживая мультитенантные среды и аутентификацию.
tags:
- Monitoring
- DevOps
- Analytics
- Search
- Database
author: Community
featured: false
---

Go-based MCP сервер, который интегрируется с Grafana Loki для запроса данных логов с использованием LogQL, поддерживая мультитенантные среды и аутентификацию.

## Установка

### Из исходного кода

```bash
# Build the server
go build -o loki-mcp-server ./cmd/server

# Run the server
./loki-mcp-server
```

### Go Run

```bash
go run ./cmd/server
```

### Docker

```bash
# Build the Docker image
docker build -t loki-mcp-server .

# Run the server
docker run --rm -i loki-mcp-server
```

### Docker Compose

```bash
# Build and run with Docker Compose
docker-compose up --build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "lokiserver": {
      "command": "path/to/loki-mcp-server",
      "args": [],
      "env": {
        "LOKI_URL": "http://localhost:3100",
        "LOKI_ORG_ID": "your-default-org-id",
        "LOKI_USERNAME": "your-username",
        "LOKI_PASSWORD": "your-password",
        "LOKI_TOKEN": "your-bearer-token"
      },
      "disabled": false,
      "autoApprove": ["loki_query"]
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "loki-mcp-server": {
      "command": "docker",
      "args": ["run", "--rm", "-i", 
               "-e", "LOKI_URL=http://host.docker.internal:3100", 
               "-e", "LOKI_ORG_ID=your-default-org-id",
               "-e", "LOKI_USERNAME=your-username",
               "-e", "LOKI_PASSWORD=your-password",
               "-e", "LOKI_TOKEN=your-bearer-token",
               "loki-mcp-server:latest"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `loki_query` | Запрос данных логов Grafana Loki с использованием LogQL с поддержкой временных диапазонов, лимитов и мультитенантности... |

## Возможности

- Запрос логов Grafana Loki с использованием синтаксиса LogQL
- Поддержка мультитенантных сред с фильтрацией по ID организации
- Несколько методов аутентификации (basic auth, bearer токен)
- Настраиваемые временные диапазоны и лимиты результатов
- Поддержка Server-Sent Events (SSE) для HTTP интеграции
- Docker контейнеризация с полной тестовой средой
- Возможности интеграции с n8n workflow
- Локальная тестовая настройка с генерацией примеров логов

## Переменные окружения

### Опциональные
- `LOKI_URL` - URL сервера Loki по умолчанию
- `LOKI_ORG_ID` - ID организации по умолчанию для мультитенантных настроек
- `LOKI_USERNAME` - Имя пользователя по умолчанию для basic аутентификации
- `LOKI_PASSWORD` - Пароль по умолчанию для basic аутентификации
- `LOKI_TOKEN` - Bearer токен по умолчанию для аутентификации
- `SSE_PORT` - Порт для HTTP сервера с поддержкой SSE

## Примеры использования

```
Query Loki for logs with the query {job="varlogs"}
```

```
Find error logs from the last hour in Loki using query {job="varlogs"} |= "ERROR"
```

```
Show me the most recent 50 logs from Loki with job=varlogs
```

```
Query Loki for logs with org 'tenant-123' using query {job="varlogs"}
```

```
Query Loki for logs from organization 'tenant-123' with the query {job="varlogs"}
```

## Ресурсы

- [GitHub Repository](https://github.com/scottlepp/loki-mcp)

## Примечания

Требуется Go 1.16 или выше. Поддерживает как stdin/stdout MCP коммуникацию, так и HTTP сервер режим с SSE. Включает полную Docker Compose настройку для локального тестирования с генерацией примеров логов. Предоставляет комплексные инструменты тестирования и CI/CD workflow.