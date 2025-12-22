---
title: Prometheus MCP сервер
description: MCP сервер, который предоставляет доступ к метрикам и запросам Prometheus, позволяя AI-ассистентам выполнять PromQL запросы и анализировать данные мониторинга.
tags:
- Monitoring
- DevOps
- Analytics
- Database
author: Community
featured: false
install_command: claude mcp add prometheus --env PROMETHEUS_URL=http://your-prometheus:9090
  -- docker run -i --rm -e PROMETHEUS_URL ghcr.io/pab1it0/prometheus-mcp-server:latest
---

MCP сервер, который предоставляет доступ к метрикам и запросам Prometheus, позволяя AI-ассистентам выполнять PromQL запросы и анализировать данные мониторинга.

## Установка

### Docker

```bash
docker run -i --rm \
  -e PROMETHEUS_URL="http://your-prometheus:9090" \
  ghcr.io/pab1it0/prometheus-mcp-server:latest
```

### Docker с аутентификацией

```bash
docker run -i --rm \
  -e PROMETHEUS_URL="http://your-prometheus:9090" \
  -e PROMETHEUS_USERNAME="admin" \
  -e PROMETHEUS_PASSWORD="password" \
  ghcr.io/pab1it0/prometheus-mcp-server:latest
```

### Из исходного кода

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv venv
source .venv/bin/activate
uv pip install -e .
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "prometheus": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "PROMETHEUS_URL",
        "ghcr.io/pab1it0/prometheus-mcp-server:latest"
      ],
      "env": {
        "PROMETHEUS_URL": "<your-prometheus-url>"
      }
    }
  }
}
```

### VS Code / Cursor / Windsurf

```json
{
  "prometheus": {
    "command": "docker",
    "args": [
      "run",
      "-i",
      "--rm",
      "-e",
      "PROMETHEUS_URL",
      "ghcr.io/pab1it0/prometheus-mcp-server:latest"
    ],
    "env": {
      "PROMETHEUS_URL": "<your-prometheus-url>"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `health_check` | Проверка состояния для мониторинга контейнера и верификации статуса |
| `execute_query` | Выполнить мгновенный PromQL запрос к Prometheus |
| `execute_range_query` | Выполнить диапазонный PromQL запрос с временем начала, окончания и интервалом шага |
| `list_metrics` | Список всех доступных метрик в Prometheus с поддержкой пагинации и фильтрации |
| `get_metric_metadata` | Получить метаданные для конкретной метрики |
| `get_targets` | Получить информацию о всех целях для сбора данных |

## Возможности

- Выполнение PromQL запросов к Prometheus
- Обнаружение и исследование метрик
- Просмотр доступных метрик
- Получение метаданных для конкретных метрик
- Просмотр результатов мгновенных запросов
- Просмотр результатов диапазонных запросов с различными интервалами шагов
- Поддержка аутентификации (Basic auth и Bearer token)
- Поддержка Docker контейнеризации
- Интерактивные инструменты для AI-ассистентов
- Настраиваемый список инструментов

## Переменные окружения

### Обязательные
- `PROMETHEUS_URL` - URL вашего сервера Prometheus

### Опциональные
- `PROMETHEUS_URL_SSL_VERIFY` - Установите False для отключения SSL верификации
- `PROMETHEUS_DISABLE_LINKS` - Установите True для отключения ссылок на Prometheus UI в результатах запросов (экономит контекстные токены)
- `PROMETHEUS_USERNAME` - Имя пользователя для базовой аутентификации
- `PROMETHEUS_PASSWORD` - Пароль для базовой аутентификации
- `PROMETHEUS_TOKEN` - Bearer токен для аутентификации
- `ORG_ID` - ID организации для мультитенантных настроек
- `PROMETHEUS_MCP_SERVER_TRANSPORT` - Режим транспорта (stdio, http, sse)
- `PROMETHEUS_MCP_BIND_HOST` - Хост для HTTP транспорта

## Ресурсы

- [GitHub Repository](https://github.com/pab1it0/prometheus-mcp-server)

## Примечания

Требует сервер Prometheus, доступный из вашего окружения, и MCP-совместимый клиент. Доступен через Docker Desktop MCP Catalog для простой установки.