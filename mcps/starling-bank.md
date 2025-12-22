---
title: Starling Bank MCP сервер
description: MCP сервер для интеграции с Starling Bank API, предоставляющий инструменты для взаимодействия с API разработчиков Starling Bank для управления счетами и транзакциями.
tags:
- Finance
- API
- Integration
author: Community
featured: false
---

MCP сервер для интеграции с Starling Bank API, предоставляющий инструменты для взаимодействия с API разработчиков Starling Bank для управления счетами и транзакциями.

## Установка

### NPX

```bash
npx -y starling-bank-mcp
```

### Ручная установка .dxt

```bash
1. Find the latest dxt build in GitHub Actions history
2. Download the mcp-server-dxt file
3. Rename the .zip file to .dxt
4. Double-click the .dxt file to open with Claude Desktop
5. Click "Install" and configure with your API key
```

### Cursor установка в один клик

```bash
Click the Install MCP Server button and edit your mcp.json file to insert your API key
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "starling-bank": {
      "command": "npx",
      "args": [
        "-y",
        "starling-bank-mcp"
      ],
      "env": {
        "STARLING_BANK_ACCESS_TOKEN": "eyJhb...",
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "starling-bank": {
      "command": "npx",
      "args": ["-y", "starling-bank-mcp"],
      "env": {
        "STARLING_BANK_ACCESS_TOKEN": "eyJhb..."
      }
    }
  }
}
```

### Cline

```json
{
  "mcpServers": {
    "starling-bank": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "starling-bank-mcp"],
      "env": {
        "STARLING_BANK_ACCESS_TOKEN": "eyJhb..."
      }
    }
  }
}
```

## Возможности

- Управление счетами через Starling Bank API
- Доступ к истории транзакций
- Возможность отправки платежей (с опциональной расширенной настройкой)
- Интеграция с Claude Desktop, Cursor и Cline

## Переменные окружения

### Обязательные
- `STARLING_BANK_ACCESS_TOKEN` - Персональный токен доступа из аккаунта Starling Bank Developer для аутентификации API

## Ресурсы

- [GitHub Repository](https://github.com/domdomegg/starling-bank-mcp)

## Примечания

Это сторонняя интеграция, не связанная с Starling Bank. Требует регистрации аккаунта Starling Developers и создания персонального токена доступа. Включает предупреждение о потенциальных рисках из-за возможных ошибок модели и prompt-инъекций при управлении банковскими счетами. Доступна опциональная настройка подписи платежей для отправки переводов.