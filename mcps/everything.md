---
title: Everything MCP сервер
description: Эталонный/тестовый сервер с промптами, ресурсами и инструментами
tags:
- Vector Database
- AI
- Media
- Messaging
- Storage
author: modelcontextprotocol
featured: true
install_command: claude mcp add everything -- npx -y @latest
---

Эталонный/тестовый сервер с промптами, ресурсами и инструментами

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `message` | (string): Сообщение для отправки обратно |
| `duration` | (number, по умолчанию: 10): Продолжительность в секундах |
| `steps` | (number, по умолчанию: 5): Количество шагов прогресса |
| `prompt` | (string): Промпт для отправки в LLM |
| `maxTokens` | (number, по умолчанию: 100): Максимальное количество токенов для генерации |
| `messageType` | (enum: "error" | "success" | "debug"): Тип сообщения для демонстрации различных ... |
| `includeImage` | (boolean, по умолчанию: false): Включать ли пример изображения |
| `resourceId` | (number, 1-100): ID ресурса для ссылки |
| `color` | (string): Любимый цвет |
| `pets` | (enum): Любимое животное |

## Ресурсы

- [GitHub Repository](https://github.com/modelcontextprotocol/servers)
- [Documentation](https://modelcontextprotocol.io)