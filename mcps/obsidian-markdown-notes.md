---
title: Obsidian Markdown Notes MCP сервер
description: Коннектор, который позволяет Claude Desktop (или любому MCP клиенту) читать и искать в любой директории с Markdown заметками, например в Obsidian хранилище.
tags:
- Productivity
- Search
- Storage
- Integration
author: smithery-ai
featured: true
---

Коннектор, который позволяет Claude Desktop (или любому MCP клиенту) читать и искать в любой директории с Markdown заметками, например в Obsidian хранилище.

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp-obsidian --client claude
```

### NPX Direct

```bash
npx -y mcp-obsidian ${input:vaultPath}
```

## Конфигурация

### VS Code User Settings

```json
{
  "mcp": {
    "inputs": [
      {
        "type": "promptString",
        "id": "vaultPath",
        "description": "Path to Obsidian vault"
      }
    ],
    "servers": {
      "obsidian": {
        "command": "npx",
        "args": ["-y", "mcp-obsidian", "${input:vaultPath}"]
      }
    }
  }
}
```

### VS Code Workspace (.vscode/mcp.json)

```json
{
  "inputs": [
    {
      "type": "promptString",
      "id": "vaultPath",
      "description": "Path to Obsidian vault"
    }
  ],
  "servers": {
    "obsidian": {
      "command": "npx",
      "args": ["-y", "mcp-obsidian", "${input:vaultPath}"]
    }
  }
}
```

## Возможности

- Чтение Markdown заметок из любой директории
- Поиск по содержимому Obsidian хранилища
- Совместимость с Claude Desktop и любым MCP клиентом
- Работа с любой директорией, содержащей Markdown файлы

## Ресурсы

- [GitHub Repository](https://github.com/calclavia/mcp-obsidian)

## Примечания

Требует установки Claude Desktop и npm. После установки через Smithery перезапустите Claude Desktop, чтобы увидеть MCP инструменты в списке. Поддерживает как VS Code, так и VS Code Insiders с кнопками установки в один клик.