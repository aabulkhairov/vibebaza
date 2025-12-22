---
title: Tempo MCP сервер
description: Основанный на Go MCP сервер, который позволяет ИИ-ассистентам запрашивать и анализировать данные распределенного трассинга из Grafana Tempo, предоставляя инструменты для поиска трассировок с помощью строк запросов Tempo.
tags:
- Monitoring
- DevOps
- Analytics
- API
author: grafana
featured: false
---

Основанный на Go MCP сервер, который позволяет ИИ-ассистентам запрашивать и анализировать данные распределенного трассинга из Grafana Tempo, предоставляя инструменты для поиска трассировок с помощью строк запросов Tempo.

## Установка

### Из исходного кода

```bash
# Build the server
go build -o tempo-mcp-server ./cmd/server

# Run the server
./tempo-mcp-server
```

### Go Run

```bash
go run ./cmd/server
```

### Docker

```bash
# Build the Docker image
docker build -t tempo-mcp-server .

# Run the server
docker run -p 8080:8080 --rm -i tempo-mcp-server
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
    "temposerver": {
      "command": "path/to/tempo-mcp-server",
      "args": [],
      "env": {
        "TEMPO_URL": "http://localhost:3200"
      },
      "disabled": false,
      "autoApprove": ["tempo_query"]
    }
  }
}
```

### Claude Desktop с Docker

```json
{
  "mcpServers": {
    "temposerver": {
      "command": "docker",
      "args": ["run", "--rm", "-i", "-e", "TEMPO_URL=http://host.docker.internal:3200", "tempo-mcp-server"],
      "disabled": false,
      "autoApprove": ["tempo_query"]
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "tempo-mcp-server": {
      "command": "docker",
      "args": ["run", "--rm", "-i", "-e", "TEMPO_URL=http://host.docker.internal:3200", "tempo-mcp-server:latest"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `tempo_query` | Запрашивает данные трассировки Grafana Tempo с поддержкой пользовательских строк запросов, временных диапазонов, лимитов и ... |

## Возможности

- Запрос данных распределенного трассинга из Grafana Tempo
- Поддержка пользовательских строк запросов Tempo
- Настраиваемые временные диапазоны и лимиты результатов
- Множественные методы аутентификации (базовая аутентификация, bearer токен)
- HTTP сервер с конечной точкой Server-Sent Events (SSE)
- Стандартная связь через stdin/stdout MCP
- Поддержка Docker для контейнеризованного развертывания
- Интеграция с ИИ-инструментами, такими как Claude Desktop, Cursor и n8n

## Переменные окружения

### Опциональные
- `TEMPO_URL` - URL сервера Tempo по умолчанию для использования, если не указан в запросе
- `SSE_PORT` - Порт для HTTP/SSE сервера (по умолчанию: 8080)

## Примеры использования

```
Query Tempo for traces with the query `{duration>1s}`
```

```
Find traces from the frontend service in Tempo using query `{service.name="frontend"}`
```

```
Show me the most recent 50 traces from Tempo with `{http.status_code=500}`
```

## Ресурсы

- [GitHub Repository](https://github.com/scottlepp/tempo-mcp-server)

## Примечания

Этот проект был архивирован. В самом Tempo теперь есть встроенный MCP сервер. Пользователи должны создавать задачи и PR в репозитории Tempo. Сервер поддерживает два режима связи: stdin/stdout и HTTP с SSE. Предварительные требования включают Go 1.21 или выше, Docker и Docker Compose для локального тестирования.