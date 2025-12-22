---
title: Pulumi MCP сервер
description: MCP сервер, который обеспечивает интеграцию с Pulumi API для программного создания и управления инфраструктурными стеками.
tags:
- DevOps
- Cloud
- API
- Integration
author: Community
featured: false
---

MCP сервер, который обеспечивает интеграцию с Pulumi API для программного создания и управления инфраструктурными стеками.

## Установка

### Docker

```bash
docker run -i --rm --name pulumi-mcp-server -e PULUMI_ACCESS_TOKEN dogukanakkaya/pulumi-mcp-server
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "pulumi-mcp-server": {
    "command": "docker",
    "args": [
      "run",
      "-i",
      "--rm",
      "--name",
      "pulumi-mcp-server",
      "-e",
      "PULUMI_ACCESS_TOKEN",
      "dogukanakkaya/pulumi-mcp-server"
    ],
    "env": {
      "PULUMI_ACCESS_TOKEN": "${YOUR_TOKEN}"
    },
    "transportType": "stdio"
  }
}
```

## Возможности

- Создание Pulumi стеков
- Просмотр существующих стеков
- Взаимодействие с Pulumi API

## Переменные окружения

### Обязательные
- `PULUMI_ACCESS_TOKEN` - Токен для аутентификации с Pulumi API

## Ресурсы

- [GitHub Repository](https://github.com/dogukanakkaya/pulumi-mcp-server)

## Примечания

Совместим с множественными MCP клиентами, включая Claude Desktop, VSCode и Cline. Процесс конфигурации схож для всех поддерживаемых клиентов.