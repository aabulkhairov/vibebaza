---
title: R mcptools MCP сервер
description: R пакет, который реализует Model Context Protocol, позволяя R функционировать как MCP сервер (давая возможность AI ассистентам выполнять R код в ваших сессиях) и как MCP клиент (интегрируя сторонние MCP серверы с R приложениями).
tags:
- Code
- AI
- Integration
- Analytics
- API
author: posit-dev
featured: true
install_command: claude mcp add -s "user" r-mcptools -- Rscript -e "mcptools::mcp_server()"
---

R пакет, который реализует Model Context Protocol, позволяя R функционировать как MCP сервер (давая возможность AI ассистентам выполнять R код в ваших сессиях) и как MCP клиент (интегрируя сторонние MCP серверы с R приложениями).

## Установка

### CRAN

```bash
install.packages("mcptools")
```

### Development версия

```bash
pak::pak("posit-dev/mcptools")
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "r-mcptools": {
      "command": "Rscript",
      "args": ["-e", "mcptools::mcp_server()"]
    }
  }
}
```

### Пример GitHub MCP сервера

```json
{
  "mcpServers": {
    "github": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "GITHUB_PERSONAL_ACCESS_TOKEN",
        "ghcr.io/github/github-mcp-server"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

## Возможности

- R как MCP сервер - позволяет AI ассистентам выполнять R код в ваших интерактивных R сессиях
- R как MCP клиент - интегрирует сторонние MCP серверы с ellmer чатами
- Совместим с Claude Desktop, Claude Code, VS Code GitHub Copilot, и Positron Assistant
- Конфигурация сессии с mcp_session() для подключения к конкретным R проектам
- Интеграция с shinychat и querychat приложениями
- Использует формат конфигурационного файла Claude Desktop для сторонних MCP серверов

## Переменные окружения

### Опциональные
- `GITHUB_PERSONAL_ACCESS_TOKEN` - персональный токен доступа GitHub для примера GitHub MCP сервера

## Примеры использования

```
From what year is the earliest recorded sample in the `forested` data in my Positron session?
```

```
What issues are open on posit-dev/mcptools?
```

## Ресурсы

- [GitHub Repository](https://github.com/posit-dev/mcptools)

## Примечания

Этот пакет ранее назывался 'acquaint'. Пользователям следует перейти с acquaint::mcp_server() на btw::btw_mcp_server() и с acquaint::mcp_session() на btw::btw_mcp_session(). Пакет хорошо интегрируется с btw пакетом для инструментов документации и инспекции окружения. Конфигурационный файл для MCP клиентов по умолчанию находится в ~/.config/mcptools/config.json.