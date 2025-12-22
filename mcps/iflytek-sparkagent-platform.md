---
title: iFlytek SparkAgent Platform MCP сервер
description: Простой MCP сервер, который предоставляет доступ к платформе iFlytek SparkAgent
  для вызова цепочек задач через Model Context Protocol.
tags:
- AI
- Integration
- API
- Productivity
author: Community
featured: false
---

Простой MCP сервер, который предоставляет доступ к платформе iFlytek SparkAgent для вызова цепочек задач через Model Context Protocol.

## Установка

### UV (stdio транспорт)

```bash
uv run ifly-spark-agent-mcp
```

### UV (SSE транспорт)

```bash
uv run ifly-spark-agent-mcp --transport sse --port 8000
```

### UVX из GitHub

```bash
uvx --from git+https://github.com/iflytek/ifly-spark-agent-mcp ifly-spark-agent-mcp
```

## Конфигурация

### Claude Desktop (UV локально)

```json
{
  "mcpServers": {
    "ifly-spark-agent-mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/ifly-spark-agent-mcp",
        "run",
        "ifly-spark-agent-mcp"
      ],
      "env": {
        "IFLY_SPARK_AGENT_BASE_URL": "xxxx",
        "IFLY_SPARK_AGENT_APP_ID": "xxxx",
        "IFLY_SPARK_AGENT_APP_SECRET": "xxxx"
      }
    }
  }
}
```

### Claude Desktop (UVX GitHub)

```json
{
    "mcpServers": {
        "ifly-spark-agent-mcp": {
            "command": "uvx",
            "args": [
                "--from",
                "git+https://github.com/iflytek/ifly-spark-agent-mcp",
                "ifly-spark-agent-mcp"
            ],
            "env": {
              "IFLY_SPARK_AGENT_BASE_URL": "xxxx",
              "IFLY_SPARK_AGENT_APP_ID": "xxxx",
              "IFLY_SPARK_AGENT_APP_SECRET": "xxxx"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `upload_file` | Принимает путь к файлу для загрузки файлов на платформу iFlytek SparkAgent |

## Возможности

- Функциональность загрузки файлов на платформу iFlytek SparkAgent
- Поддержка как stdio, так и SSE транспортных протоколов
- Интеграция с цепочками задач iFlytek SparkAgent

## Переменные окружения

### Обязательные
- `IFLY_SPARK_AGENT_BASE_URL` - Базовый URL для API платформы iFlytek SparkAgent
- `IFLY_SPARK_AGENT_APP_ID` - ID приложения для аутентификации iFlytek SparkAgent
- `IFLY_SPARK_AGENT_APP_SECRET` - Секретный ключ приложения для аутентификации iFlytek SparkAgent

## Примеры использования

```
Загрузите файл на платформу iFlytek SparkAgent используя инструмент upload_file
```

## Ресурсы

- [GitHub Repository](https://github.com/iflytek/ifly-spark-agent-mcp)

## Примечания

Этот сервер предоставляет простой интерфейс к платформе iFlytek SparkAgent. Сервер поддерживает как stdio (по умолчанию), так и SSE транспортные протоколы. Аутентификация требует правильной настройки трех переменных окружения для API SparkAgent.