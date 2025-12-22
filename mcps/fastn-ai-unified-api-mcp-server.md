---
title: fastn.ai – Unified API MCP сервер
description: Мультитенантный MCP сервер, который предоставляет доступ к более чем 1000 SaaS инструментов (Slack, Jira, Gmail, Shopify, Notion и другие) через единую стандартизированную конечную точку команд, абстрагируя сложность SDK и потоки аутентификации.
tags:
- Integration
- API
- Productivity
- CRM
- Messaging
author: Community
featured: false
---

Мультитенантный MCP сервер, который предоставляет доступ к более чем 1000 SaaS инструментов (Slack, Jira, Gmail, Shopify, Notion и другие) через единую стандартизированную конечную точку команд, абстрагируя сложность SDK и потоки аутентификации.

## Установка

### Установка пакета

```bash
pip install fastn-mcp-server
```

### Из исходного кода

```bash
git clone <your-repo-url> && cd fastn-server
curl -LsSf https://astral.sh/uv/install.sh | sh && uv venv && source .venv/bin/activate && uv pip install -e .
uv pip install "httpx>=0.28.1" "mcp[cli]>=1.2.0"
```

### Docker

```bash
docker-compose up --build
```

## Конфигурация

### Claude Desktop (установка пакета)

```json
{
  "mcpServers": {
    "fastn": {
      "command": "/path/to/fastn-mcp-server",
      "args": [
        "--api_key",
        "YOUR_API_KEY",
        "--space_id",
        "YOUR_WORKSPACE_ID"
      ]
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "ucl": {
      "command": "docker",
      "args": [
        "run", "-i", "--rm",
        "--env-file", "/path/to/your/fastn-stdio-server/.env",
        "ucl-stdio-server"
      ]
    }
  }
}
```

## Возможности

- Интегрированная поддержка платформ для сервисов типа Slack, Notion, HubSpot и многих других
- Гибкая аутентификация с опциями API ключа или на основе тенанта
- Комплексное логирование для устранения неполадок
- Надежное управление ошибками для различных сценариев
- Доступ к более чем 1000 SaaS инструментов через единую конечную точку
- Мультитенантная поддержка
- Абстрагирует проблему разрастания SDK и сложные потоки аутентификации

## Переменные окружения

### Обязательные
- `SPACE_ID` - Ваш UCL workspace/space ID

### Опциональные
- `API_KEY` - Ваш UCL API ключ для аутентификации
- `TENANT_ID` - Ваш tenant ID для аутентификации на основе тенанта
- `AUTH_TOKEN` - Токен аутентификации для аутентификации на основе тенанта
- `CONFIG_MODE` - Режим конфигурации: 'basic' или 'extended'

## Ресурсы

- [GitHub Repository](https://github.com/fastnai/mcp-fastn)

## Примечания

Требует Python 3.10 или выше. Необходима настройка UCL аккаунта с активацией сервиса через UCL панель управления. Поддерживает как API ключ, так и методы аутентификации на основе тенанта. Доступна интеграция для Claude и Cursor AI ассистентов.