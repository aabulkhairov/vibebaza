---
title: Cursor MCP Installer MCP сервер
description: Model Context Protocol (MCP) сервер для установки и конфигурации других MCP серверов в Cursor IDE, с поддержкой npm пакетов, локальных директорий и Git репозиториев.
tags:
- Productivity
- Integration
- DevOps
- Code
author: matthewdcage
featured: false
---

Model Context Protocol (MCP) сервер для установки и конфигурации других MCP серверов в Cursor IDE, с поддержкой npm пакетов, локальных директорий и Git репозиториев.

## Установка

### NPM Global

```bash
npm install -g cursor-mcp-installer-free@0.1.3
```

### Из исходников

```bash
git clone https://github.com/matthewdcage/cursor-mcp-installer.git
cd cursor-mcp-installer
npm install
npm run build
```

## Конфигурация

### Cursor NPX

```json
{
  "mcpServers": {
    "MCP Installer": {
      "command": "npx",
      "type": "stdio",
      "args": [
        "cursor-mcp-installer-free@0.1.3",
        "index.mjs"
      ]
    }
  }
}
```

### Cursor NPM Global

```json
{
  "mcpServers": {
    "MCP Installer": {
      "command": "cursor-mcp-installer-free",
      "type": "stdio",
      "args": [
        "index.mjs"
      ]
    }
  }
}
```

### Cursor локальная сборка

```json
{
  "mcpServers": {
    "MCP Installer": {
      "command": "node",
      "type": "stdio",
      "args": [
        "/path/to/cursor-mcp-installer/lib/index.mjs"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `install_repo_mcp_server` | Установка MCP серверов из npm пакетов или репозиториев |
| `install_local_mcp_server` | Установка MCP серверов из локальных директорий |
| `add_to_cursor_config` | Добавление пользовательских конфигураций MCP серверов |

## Возможности

- Установка MCP серверов из npm пакетов
- Установка MCP серверов из локальных директорий
- Конфигурация MCP серверов для Cursor
- Добавление пользовательских конфигураций MCP серверов
- Улучшенное разрешение путей с поддержкой пробелов и специальных символов
- Лучшее обнаружение OpenAPI схем с поддержкой множественных расширений файлов
- Улучшенное обнаружение серверов для MCP серверов на основе Python

## Примеры использования

```
Install the web search MCP server
```

```
Install the MCP server for OpenAPI schema exploration with my-schema.yaml
```

```
Install the MCP server named mcp-server-fetch
```

```
Install the @modelcontextprotocol/server-filesystem package as an MCP server. Use ['/home/user/documents'] for the arguments
```

```
Install the MCP server at /home/user/projects/my-mcp-server
```

## Ресурсы

- [GitHub Repository](https://github.com/matthewdcage/cursor-mcp-installer)

## Примечания

Расположение файла конфигурации: ~/.cursor/mcp.json (macOS/Linux) или %USERPROFILE%\.cursor\mcp.json (Windows). Может использоваться с npx без глобальной установки. Версия 0.1.3 включает улучшенную обработку путей и лучшее обнаружение схем.