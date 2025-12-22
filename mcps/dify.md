---
title: Dify MCP сервер
description: MCP сервер, который позволяет вызывать рабочие процессы Dify через инструменты MCP,
  обеспечивая интеграцию с облачными платформами Dify.
tags:
- AI
- Integration
- API
- Cloud
- Productivity
author: YanxingLiu
featured: true
---

MCP сервер, который позволяет вызывать рабочие процессы Dify через инструменты MCP, обеспечивая интеграцию с облачными платформами Dify.

## Установка

### UVX (Рекомендуется)

```bash
uvx --from git+https://github.com/YanxingLiu/dify-mcp-server dify_mcp_server
```

### UV (Локальное клонирование)

```bash
uv --directory ${DIFY_MCP_SERVER_PATH} run dify_mcp_server
```

### Установка UV

```bash
curl -Ls https://astral.sh/uv/install.sh | sh
```

## Конфигурация

### UVX с переменными окружения

```json
{
"mcpServers": {
  "dify-mcp-server": {
    "command": "uvx",
      "args": [
        "--from","git+https://github.com/YanxingLiu/dify-mcp-server","dify_mcp_server"
      ],
    "env": {
       "DIFY_BASE_URL": "https://cloud.dify.ai/v1",
       "DIFY_APP_SKS": "app-sk1,app-sk2"
    }
  }
}
}
```

### UVX с конфигурационным файлом

```json
{
"mcpServers": {
  "dify-mcp-server": {
    "command": "uvx",
      "args": [
        "--from","git+https://github.com/YanxingLiu/dify-mcp-server","dify_mcp_server"
      ],
    "env": {
       "CONFIG_PATH": "/Users/lyx/Downloads/config.yaml"
    }
  }
}
}
```

### UV локально с переменными окружения

```json
{
"mcpServers": {
  "dify-mcp-server": {
    "command": "uv",
      "args": [
        "--directory", "/Users/lyx/Downloads/dify-mcp-server",
        "run", "dify_mcp_server"
      ],
    "env": {
       "DIFY_BASE_URL": "https://cloud.dify.ai/v1",
       "DIFY_APP_SKS": "app-sk1,app-sk2"
    }
  }
}
}
```

## Возможности

- Вызов рабочих процессов Dify через инструменты MCP
- Поддержка конфигурации через переменные окружения
- Поддержка YAML конфигурационных файлов
- Интеграция с облачными платформами Dify
- Поддержка нескольких секретных ключей приложений для различных рабочих процессов

## Переменные окружения

### Обязательные
- `DIFY_BASE_URL` - Базовый URL для вашего Dify API (например, https://cloud.dify.ai/v1)
- `DIFY_APP_SKS` - Список секретных ключей приложений Dify (SKs), разделенный запятыми, каждый соответствует отдельному рабочему процессу

### Опциональные
- `CONFIG_PATH` - Путь к файлу config.yaml (альтернатива переменным окружения)

## Ресурсы

- [GitHub Repository](https://github.com/YanxingLiu/dify-mcp-server)

## Примечания

Сервер поддерживает два метода конфигурации: переменные окружения (рекомендуется для облачных платформ) или файл config.yaml. Каждый секретный ключ приложения Dify соответствует отдельному рабочему процессу. Доступен через Smithery по адресу https://smithery.ai/server/dify-mcp-server. Недавнее обновление (2025/4/15) добавило прямую поддержку переменных окружения для облачных платформ.