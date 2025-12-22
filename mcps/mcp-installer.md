---
title: MCP Installer MCP сервер
description: MCP сервер, который устанавливает другие MCP серверы за вас, позволяя попросить Claude установить MCP серверы, размещённые в npm или PyPi.
tags:
- Integration
- DevOps
- Productivity
- API
author: anaisbetts
featured: true
---

MCP сервер, который устанавливает другие MCP серверы за вас, позволяя попросить Claude установить MCP серверы, размещённые в npm или PyPi.

## Установка

### NPX

```bash
npx @anaisbetts/mcp-installer
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "mcp-installer": {
      "command": "npx",
      "args": [
        "@anaisbetts/mcp-installer"
      ]
    }
  }
}
```

## Возможности

- Установка MCP серверов из npm
- Установка MCP серверов из PyPi
- Установка локальных MCP серверов по файловым путям
- Настройка аргументов сервера во время установки
- Установка переменных окружения для установленных серверов

## Примеры использования

```
Hey Claude, install the MCP server named mcp-server-fetch
```

```
Hey Claude, install the @modelcontextprotocol/server-filesystem package as an MCP server. Use ['/Users/anibetts/Desktop'] for the arguments
```

```
Hi Claude, please install the MCP server at /Users/anibetts/code/mcp-youtube, I'm too lazy to do it myself.
```

```
Install the server @modelcontextprotocol/server-github. Set the environment variable GITHUB_PERSONAL_ACCESS_TOKEN to '1234567890'
```

## Ресурсы

- [GitHub Repository](https://github.com/anaisbetts/mcp-installer)

## Примечания

Требует установки npx и uv для серверов node и Python соответственно.