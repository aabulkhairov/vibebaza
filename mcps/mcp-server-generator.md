---
title: MCP Server Generator MCP сервер
description: MCP сервер для создания других MCP серверов с помощью ИИ — автоматически генерирует кастомные JavaScript MCP серверы с управлением зависимостями и интеграцией в Claude Desktop.
tags:
- Code
- DevOps
- Productivity
- Integration
- AI
author: SerhatUzbas
featured: false
---

MCP сервер для создания и управления другими MCP серверами, который помогает разрабатывать кастомные JavaScript MCP серверы с помощью ИИ, автоматическим управлением зависимостями и интеграцией в Claude Desktop.

## Установка

### Из исходного кода

```bash
git clone https://github.com/SerhatUzbas/mcp-server-generator.git
cd mcprotocol
npm install
```

## Конфигурация

### Claude Desktop (macOS/Linux)

```json
{
  "mcpServers": {
    "mcp-server-generator": {
      "command": "node",
      "args": ["/Users/username/Documents/GitHub/mcprotocol/creator-server.js"]
    }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "mcp-server-generator": {
      "command": "node",
      "args": ["C:\\Users\\username\\Documents\\GitHub\\mcprotocol\\creator-server.js"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `listServers` | Список всех доступных серверов |
| `getServerContent` | Просмотр кода существующего сервера |
| `createMcpServer` | Создание нового сервера |
| `updateMcpServer` | Обновление существующего сервера |
| `analyzeServerDependencies` | Определение необходимых npm пакетов |
| `installServerDependencies` | Установка необходимых пакетов |
| `getClaudeConfig` | Просмотр текущей конфигурации Claude Desktop |
| `updateClaudeConfig` | Обновление конфигурации Claude Desktop |
| `runServerDirectly` | Проверка на наличие ошибок при запуске |

## Возможности

- Создание новых MCP серверов
- Обновление существующих серверов
- Регистрация серверов в Claude Desktop
- Генерация серверов с помощью ИИ
- Автоматическое управление зависимостями
- Анализ и валидация кода серверов
- Управление конфигурацией Claude Desktop

## Примеры использования

```
Создай простой MCP сервер для интеграции с PostgreSQL, который предоставляет операции с базой данных и возможности выполнения запросов.
```

## Ресурсы

- [GitHub Repository](https://github.com/SerhatUzbas/mcp-server-generator)

## Примечания

Требования: Node.js версии 16 или выше и установленный Claude Desktop. Пользователям Windows нужно использовать обратные слэши для путей к файлам и правильно экранировать их в JSON конфигурации. После регистрации новых серверов необходимо перезапустить Claude Desktop.