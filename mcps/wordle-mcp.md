---
title: Wordle MCP сервер
description: MCP сервер для получения решений Wordle через Wordle API для дат с 2021-05-19 до 23 дней в будущем.
tags:
- API
- Web Scraping
- Productivity
author: cr2007
featured: false
---

MCP сервер для получения решений Wordle через Wordle API для дат с 2021-05-19 до 23 дней в будущем.

## Установка

### Docker (рекомендуется)

```bash
docker pull ghcr.io/cr2007/mcp-wordle-python:latest
```

### uvx

```bash
uvx --from git+https://github.com/cr2007/mcp-wordle-python mcp-wordle
```

## Конфигурация

### Конфигурация Docker

```json
{
  "mcpServers": {
    "Wordle MCP (Python)": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "--init",
        "-e",
        "DOCKER_CONTAINER=true",
        "ghcr.io/cr2007/mcp-wordle-python:latest"
      ]
    }
  }
}
```

### Конфигурация uvx

```json
{
  "mcpServers": {
    "Wordle MCP (Python)":{
      "command": "uvx",
        "args": [
          "--from",
          "git+https://github.com/cr2007/mcp-wordle-python",
          "mcp-wordle"
        ]
      }
  }
}
```

## Возможности

- Получение решений Wordle для конкретных дат
- Доступ к решениям с 2021-05-19
- Поддержка решений до 23 дней в будущем
- Контейнеризированный деплой через Docker
- Доступна Go версия для более легкой/быстрой работы

## Переменные окружения

### Обязательные
- `DOCKER_CONTAINER` - Установите в true при запуске в Docker контейнере

## Ресурсы

- [GitHub Repository](https://github.com/cr2007/mcp-wordle-python)

## Примечания

Решения Wordle доступны только с 2021-05-19 до 23 дней в будущем. Любые попытки запросить другие даты вернут ошибку API. Также доступна Go версия для лучшей производительности: https://github.com/cr2007/mcp-wordle-go