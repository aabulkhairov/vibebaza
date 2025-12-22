---
title: Slidespeak MCP сервер
description: MCP сервер, который позволяет создавать PowerPoint презентации с помощью SlideSpeak API для автоматизации отчетов, презентаций и других слайдовых колод.
tags:
- Productivity
- API
- Media
author: SlideSpeak
featured: false
---

MCP сервер, который позволяет создавать PowerPoint презентации с помощью SlideSpeak API для автоматизации отчетов, презентаций и других слайдовых колод.

## Установка

### Remote MCP (NPX)

```bash
npx mcp-remote https://mcp.slidespeak.co/mcp --header "Authorization: Bearer YOUR-SLIDESPEAK-API-KEY-HERE"
```

### Docker

```bash
docker run -i --rm -e SLIDESPEAK_API_KEY slidespeak/slidespeak-mcp:latest
```

### Из исходного кода

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop (Remote MCP)

```json
{
  "mcpServers": {
    "slidespeak": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.slidespeak.co/mcp",
        "--header",
        "Authorization: Bearer YOUR-SLIDESPEAK-API-KEY-HERE"
      ],
      "timeout": 300000
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "slidespeak": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "SLIDESPEAK_API_KEY",
        "slidespeak/slidespeak-mcp:latest"
      ],
      "env": {
        "SLIDESPEAK_API_KEY": "YOUR-SLIDESPEAK-API-KEY-HERE"
      }
    }
  }
}
```

### Claude Desktop (Прямое подключение)

```json
{
  "mcpServers": {
    "slidespeak": {
      "command": "/path/to/.local/bin/uv",
      "args": [
        "--directory",
        "/path/to/slidespeak-mcp",
        "run",
        "slidespeak.py"
      ],
      "env": {
        "SLIDESPEAK_API_KEY": "API-KEY-HERE"
      }
    }
  }
}
```

## Возможности

- Создание PowerPoint презентаций
- Автоматизация отчетов и слайдовых колод
- Интеграция с SlideSpeak API
- Поддержка нескольких методов развертывания (Remote, Docker, прямое подключение)

## Переменные окружения

### Обязательные
- `SLIDESPEAK_API_KEY` - API ключ для доступа к сервисам SlideSpeak

## Ресурсы

- [GitHub Repository](https://github.com/SlideSpeak/slidespeak-mcp)

## Примечания

Требуется API ключ SlideSpeak, который можно получить на https://slidespeak.co/slidespeak-api/. Подход Remote MCP требует Node.js, а подход Docker требует Docker Desktop. Сервер имеет таймаут в 300 секунд для операций.