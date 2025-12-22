---
title: 1mcpserver MCP сервер
description: Мета-MCP сервер, который автоматически находит, выбирает и настраивает
  другие MCP серверы за тебя. Избавляет от необходимости вручную искать, устанавливать
  и конфигурировать отдельные MCP серверы.
tags:
- Integration
- Productivity
- API
- DevOps
- Search
author: particlefuture
featured: false
---

Мета-MCP сервер, который автоматически находит, выбирает и настраивает другие MCP серверы за тебя. Избавляет от необходимости вручную искать, устанавливать и конфигурировать отдельные MCP серверы.

## Установка

### Удалённая настройка

```bash
Add configuration to ~/.cursor/mcp.json or Claude desktop config - no installation required
```

### Из исходников

```bash
git clone https://github.com/particlefuture/MCPDiscovery.git
cd MCPDiscovery
uv sync
uv run server.py
```

## Конфигурация

### Удалённая настройка (Claude/Cursor)

```json
{
  "mcpServers": {
    "mcp-server-discovery": {
      "url": "https://mcp.1mcpserver.com/mcp/",
      "headers": {
        "Accept": "text/event-stream",
        "Cache-Control": "no-cache",
        "API_KEY": "value"
      }
    }
  }
}
```

### Локальная STDIO настройка

```json
{
  "mcpServers": {
    "mcp-servers-discovery": {
      "command": "/Users/jiazhenghao/.local/bin/uv",
      "args": [
        "--directory",
        "{PATH_TO_THE_CLONED_REPO}",
        "run",
        "server.py",
        "--local"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `quick_search` | Возвращает список MCP серверов для конкретных целей |
| `deep_search` | Разбивает сложные задачи на компоненты и находит подходящие MCP серверы |
| `test_server_template_code` | Возвращает примеры тестового кода для проверки работы MCP серверов |

## Возможности

- Автоматическое обнаружение и конфигурация MCP серверов
- Не нужны ручные команды установки или получение API ключей
- Быстрый поиск для конкретных требований к MCP серверам
- Глубокий поиск с агентным планированием для сложных задач
- Автоматическая настройка API ключей и инструкции по установке
- Обработка модификации файла mcp.json
- Возможности тестирования серверов
- Построение многошаговых workflow с использованием найденных MCP серверов

## Переменные окружения

### Опциональные
- `API_KEY` — API ключ для доступа к удалённому серверу

## Примеры использования

```
I want a MCP server that handles payment
```

```
Build me a website that analyzes other websites
```

## Ресурсы

- [GitHub Repository](https://github.com/particlefuture/1mcpserver)

## Примечания

Демо-видео доступно на https://youtu.be/W4EAmaTTb2A. Сервер выполняет горизонтальное расширение для независимых компонентов и вертикальное расширение для последовательных шагов. Включает этапы планирования, тестирования и выполнения для сложных workflow.
