---
title: mcp-proxy MCP сервер
description: Go реализация прокси-сервера, который соединяет MCP клиенты с удаленными MCP серверами с поддержкой OAuth 2.0, обеспечивая аутентификацию и управление токенами для клиентов без нативной поддержки OAuth.
tags:
- Security
- API
- Integration
- Productivity
- DevOps
author: mikluko
featured: false
install_command: claude mcp add remote-example mcp-proxy https://remote.mcp.server/sse
---

Go реализация прокси-сервера, который соединяет MCP клиенты с удаленными MCP серверами с поддержкой OAuth 2.0, обеспечивая аутентификацию и управление токенами для клиентов без нативной поддержки OAuth.

## Установка

### Homebrew

```bash
brew install mikluko/tap/mcp-proxy
```

### Go

```bash
go install github.com/mikluko/mcp-proxy/cmd/mcp-proxy@latest
```

### Бинарные релизы

```bash
Download from GitHub Releases: https://github.com/mikluko/mcp-proxy/releases
```

## Конфигурация

### Claude Desktop, Cursor, Windsurf

```json
{
  "mcpServers": {
    "remote-example": {
      "command": "mcp-proxy",
      "args": [
        "https://remote.mcp.server/sse"
      ]
    }
  }
}
```

### Пользовательские заголовки

```json
{
  "mcpServers": {
    "remote-example": {
      "command": "mcp-proxy",
      "args": [
        "https://remote.mcp.server/sse",
        "--header",
        "Authorization:Bearer ${AUTH_TOKEN}"
      ],
      "env": {
        "AUTH_TOKEN": "your-token"
      }
    }
  }
}
```

### Множественные экземпляры

```json
{
  "mcpServers": {
    "tenant1": {
      "command": "mcp-proxy",
      "args": [
        "https://mcp.example.com/sse",
        "--resource",
        "https://tenant1.example.com/"
      ]
    },
    "tenant2": {
      "command": "mcp-proxy",
      "args": [
        "https://mcp.example.com/sse",
        "--resource",
        "https://tenant2.example.com/"
      ]
    }
  }
}
```

## Возможности

- Двойной режим работы: Stdio (по умолчанию) или HTTP/SSE сервер
- OAuth 2.0: Полная поддержка с PKCE, динамическая регистрация клиентов и обновление токенов
- Гибкость транспорта: HTTP и SSE с настраиваемыми стратегиями fallback
- Фильтрация инструментов: Блокировка определенных инструментов от доступа клиентам
- Поддержка пользовательских заголовков
- Множественные стратегии транспорта (http-first, sse-first, http-only, sse-only)
- Кроссплатформенное управление директориями кэша
- Автоматическое обновление токенов при истечении срока

## Переменные окружения

### Опциональные
- `AUTH_TOKEN` - Токен аутентификации для пользовательских заголовков
- `HTTP_PROXY/HTTPS_PROXY` - Настройки HTTP прокси (при использовании флага --enable-proxy)

## Ресурсы

- [GitHub Repository](https://github.com/mikluko/mcp-proxy)

## Примечания

OAuth токены и регистрация клиентов хранятся в специфичных для платформы директориях кэша. Прокси может работать в режиме HTTP сервера для веб-клиентов или совместного использования upstream соединений. Стратегия транспорта контролирует поведение fallback между HTTP и SSE соединениями.