---
title: Discogs MCP сервер
description: MCP сервер для подключения к Discogs API, который обеспечивает работу с музыкальным каталогом, функциональность поиска и управление коллекциями на платформе музыкальной базы данных.
tags:
- API
- Media
- Database
- Search
- Integration
author: cswkim
featured: false
---

MCP сервер для подключения к Discogs API, который обеспечивает работу с музыкальным каталогом, функциональность поиска и управление коллекциями на платформе музыкальной базы данных.

## Установка

### NPX

```bash
npx -y discogs-mcp-server
```

### Из исходников

```bash
git clone https://github.com/cswkim/discogs-mcp-server
cd discogs-mcp-server
pnpm install
pnpm run dev
```

### Docker

```bash
docker build -t discogs-mcp-server:latest .
docker run --env-file .env discogs-mcp-server:latest
```

## Конфигурация

### Claude Desktop NPX

```json
{
  "mcpServers": {
    "discogs": {
      "command": "npx",
      "args": [
        "-y",
        "discogs-mcp-server"
      ],
      "env": {
        "DISCOGS_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

### Claude Desktop Local Node

```json
{
  "mcpServers": {
    "discogs": {
      "command": "npx",
      "args": [
        "tsx",
        "/PATH/TO/YOUR/PROJECT/FOLDER/src/index.ts"
      ],
      "env": {
        "DISCOGS_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

### Claude Desktop Docker

```json
{
  "mcpServers": {
    "discogs": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "--env-file",
        "/PATH/TO/YOUR/PROJECT/FOLDER/.env",
        "discogs-mcp-server:latest"
      ]
    }
  }
}
```

### LibreChat

```json
discogs:
  type: stdio
  command: npx
  args: ["-y", "discogs-mcp-server"]
  env:
    DISCOGS_PERSONAL_ACCESS_TOKEN: YOUR_TOKEN_GOES_HERE
```

## Возможности

- Операции с музыкальным каталогом через Discogs API
- Функциональность поиска релизов, исполнителей и лейблов
- Возможности управления и редактирования коллекций
- Построен на фреймворке FastMCP typescript
- Поддержка нескольких MCP клиентов (Claude, LibreChat, LM Studio)
- Docker поддержка для контейнерного деплоя
- Интеграция с MCP Inspector для тестирования

## Переменные окружения

### Обязательные
- `DISCOGS_PERSONAL_ACCESS_TOKEN` - Ваш персональный токен доступа Discogs для аутентификации API

### Опциональные
- `SERVER_HOST` - Адрес хоста для привязки сервера (по умолчанию: 0.0.0.0)

## Ресурсы

- [GitHub Repository](https://github.com/cswkim/discogs-mcp-server)

## Примечания

В документации Discogs API есть некоторые несоответствия. Сервер позволяет редактировать данные коллекции, поэтому используйте с осторожностью. По умолчанию per_page установлен в 5 для лучшей совместимости с клиентами (против стандартного значения Discogs API в 50). Требуется персональный токен доступа Discogs из настроек разработчика. OAuth поддержка запланирована для будущего релиза.