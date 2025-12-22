---
title: Peacock for VS Code MCP сервер
description: MCP сервер для расширения Peacock в VS Code, который предоставляет доступ к документации Peacock и помощь с конфигурацией для кастомизации цветов и тем VS Code.
tags:
- Code
- Productivity
- API
- Integration
author: Community
featured: false
---

MCP сервер для расширения Peacock в VS Code, который предоставляет доступ к документации Peacock и помощь с конфигурацией для кастомизации цветов и тем VS Code.

## Установка

### NPX

```bash
npx -y @johnpapa/peacock-mcp
```

### Docker

```bash
docker run -i --rm mcp/peacock-mcp
```

### VS Code CLI (Stable)

```bash
code --add-mcp '{"name":"peacock-mcp","command":"npx","args":["-y","@johnpapa/peacock-mcp"],"env":{}}'
```

### VS Code CLI (Insiders)

```bash
code-insiders --add-mcp '{"name":"peacock-mcp","command":"npx","args":["-y","@johnpapa/peacock-mcp"],"env":{}}'
```

### Smithery

```bash
npx -y @smithery/cli install @johnpapa/peacock-mcp --client claude
```

## Конфигурация

### VS Code (Репозиторий-специфичный .vscode/mcp.json)

```json
{
  "inputs": [],
  "servers": {
    "peacock-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "@johnpapa/peacock-mcp"
      ],
      "env": {}
    }
  }
}
```

### Пользовательские настройки VS Code

```json
{
  "mcp": {
    "servers": {
      "peacock-mcp": {
        "command": "npx",
        "args": [
          "-y",
          "@johnpapa/peacock-mcp"
        ],
        "env": {}
      }
    }
  },
  "chat.mcp.discovery.enabled": true
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `fetch_peacock_docs` | Получает документацию расширения Peacock for VS Code из его GitHub репозитория и отвечает на вопросы... |

## Возможности

- Получение документации Peacock и предоставление подробной информации
- Ответы на вопросы о функциональности расширения Peacock
- Интеграция с VS Code через протокол MCP
- Доступ к официальным данным документации Peacock

## Примеры использования

```
Как мне настроить акцентные цвета VS Code?
```

## Ресурсы

- [GitHub Repository](https://github.com/johnpapa/peacock-mcp)

## Примечания

Основная цель проекта — показать, как MCP сервер может быть использован для взаимодействия с API. Все данные, используемые этим MCP сервером, получаются из официальной документации Peacock. Требует Node.js >=20. Для интеграции с VS Code используйте режим Agent в GitHub Copilot и обновите список серверов для доступа к инструментам.