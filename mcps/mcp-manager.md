---
title: mcp-manager MCP сервер
description: Desktop приложение для управления серверами Model Context Protocol (MCP) для Claude Desktop на MacOS, предоставляющее удобный интерфейс для установки и настройки популярных MCP серверов.
tags:
- Productivity
- Integration
- API
- DevOps
author: zueai
featured: true
---

Desktop приложение для управления серверами Model Context Protocol (MCP) для Claude Desktop на MacOS, предоставляющее удобный интерфейс для установки и настройки популярных MCP серверов.

## Установка

### Настройка для разработки

```bash
bun install
bun electron:dev
```

### Сборка для MacOS

```bash
rm -rf dist dist-electron
bun electron:build
```

## Возможности

- Удобный desktop интерфейс для управления MCP серверами
- Работает локально - ваши данные никогда не покидают компьютер
- Быстрая настройка для 22+ популярных MCP серверов, включая Apple Notes, GitHub, Google Drive, PostgreSQL и другие
- Простая конфигурация переменных окружения и настроек сервера
- Копирование команд для терминала одним кликом для установки

## Ресурсы

- [GitHub Repository](https://github.com/zueai/mcp-manager)

## Примечания

Создан с использованием Electron, React и TypeScript. Поддерживает популярные MCP серверы такие как Apple Notes, AWS Knowledge Base, Brave Search, Browserbase, Cloudflare, GitHub, Google Drive, PostgreSQL, Slack и многие другие. Проект не аффилирован с Anthropic и распространяется с открытым исходным кодом под лицензией MIT.