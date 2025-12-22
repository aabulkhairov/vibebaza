---
title: OpenRPC MCP сервер
description: MCP сервер, который предоставляет функциональность JSON-RPC через OpenRPC, позволяя вызывать произвольные JSON-RPC методы и обнаруживать доступные методы на удаленных серверах.
tags:
- API
- Integration
- Code
- DevOps
author: shanejonas
featured: false
---

MCP сервер, который предоставляет функциональность JSON-RPC через OpenRPC, позволяя вызывать произвольные JSON-RPC методы и обнаруживать доступные методы на удаленных серверах.

## Установка

### NPX

```bash
npx -y openrpc-mcp-server
```

### Из исходного кода

```bash
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "openrpc": {
      "command": "npx",
      "args": ["-y", "openrpc-mcp-server"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `rpc_call` | Вызов произвольных JSON-RPC методов с указанием URL сервера, имени метода и параметров, возвращает ... |
| `rpc_discover` | Обнаружение доступных JSON-RPC методов с использованием OpenRPC спецификации rpc.discover для перечисления всех методов... |

## Возможности

- Вызов произвольных JSON-RPC методов
- Обнаружение доступных JSON-RPC методов через OpenRPC спецификацию
- Возврат результатов в JSON формате
- Поддержка OpenRPC спецификации rpc.discover

## Ресурсы

- [GitHub Repository](https://github.com/shanejonas/openrpc-mpc-server)

## Примечания

Пути конфигурации: на MacOS в ~/Library/Application Support/Claude/claude_desktop_config.json, на Windows в %APPDATA%/Claude/claude_desktop_config.json. Отладка доступна через MCP Inspector с помощью команды 'npm run inspector'. Режим разработки доступен с 'npm run watch' для автоматической пересборки.