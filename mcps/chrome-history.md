---
title: Chrome history MCP сервер
description: MCP сервер, который предоставляет историю браузера Chrome для работы с AI, позволяя общаться с искусственным интеллектом о вашей истории просмотров.
tags:
- Browser
- AI
- Productivity
- Database
author: vincent-pli
featured: false
---

MCP сервер, который предоставляет историю браузера Chrome для работы с AI, позволяя общаться с искусственным интеллектом о вашей истории просмотров.

## Установка

### UV Run (путь по умолчанию)

```bash
uv run chrome-history-mcp
```

### UV Run (пользовательский путь)

```bash
uv run chrome-history-mcp --path /Users/lipeng/Library/Application\ Support/Google/Chrome/Profile\ 3/History
```

## Конфигурация

### MCP CLI Host

```json
{
  "mcpServers": {
    "a2a-mcp": {
      "command": "uv",
      "args": [
        "--project",
        "<location of the repo>",
        "run",
        "chrome-history-mcp",
        "--path",
        "<location of your chrome history>"
      ]
    }
  }
}
```

## Возможности

- Доступ к данным истории браузера Chrome
- Поддержка множественных профилей Chrome
- Кроссплатформенная поддержка (Windows, macOS, Linux)
- Настраиваемый путь к истории Chrome

## Ресурсы

- [GitHub Repository](https://github.com/vincent-pli/chrome-history-mcp)

## Примечания

Пути к истории Chrome по умолчанию: Windows: C:\Users\<username>\AppData\Local\Google\Chrome\User Data\Default, macOS: /Users/<username>/Library/Application Support/Google/Chrome/Default, Linux: /home/<username>/.config/google-chrome/Default. Используйте флаг --path для пользовательских расположений профилей Chrome.