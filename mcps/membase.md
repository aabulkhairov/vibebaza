---
title: Membase MCP сервер
description: Membase — это децентрализованный слой памяти для AI агентов, который обеспечивает безопасное, постоянное хранение истории разговоров, записей взаимодействий и знаний с использованием сети Unibase DA.
tags:
- Storage
- AI
- Database
- Messaging
- Integration
author: unibaseio
featured: false
---

Membase — это децентрализованный слой памяти для AI агентов, который обеспечивает безопасное, постоянное хранение истории разговоров, записей взаимодействий и знаний с использованием сети Unibase DA.

## Установка

### Из исходного кода

```bash
git clone https://github.com/unibaseio/membase-mcp.git
cd membase-mcp
uv run src/membase_mcp/server.py
```

## Конфигурация

### Claude/Windsurf/Cursor/Cline

```json
{
  "mcpServers": {
    "membase": {
      "command": "uv",
      "args": [
        "--directory",
        "path/to/membase-mcp",
        "run", 
        "src/membase_mcp/server.py"
      ],
      "env": {
        "MEMBASE_ACCOUNT": "your account, 0x...",
        "MEMBASE_CONVERSATION_ID": "your conversation id, should be unique",
        "MEMBASE_ID": "your sub account, any string"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_conversation_id` | Получить текущий ID разговора |
| `switch_conversation` | Переключиться на другой разговор |
| `save_message` | Сохранить сообщение/память в текущий разговор |
| `get_messages` | Получить последние n сообщений из текущего разговора |

## Возможности

- Децентрализованный слой памяти для AI агентов
- Безопасное, постоянное хранение истории разговоров
- Интеграция с сетью Unibase DA
- Верифицируемые возможности хранения
- Непрерывность работы агентов и персонализация
- Управление разговорами и переключение между ними
- Сохранение и получение сообщений/памяти

## Переменные окружения

### Обязательные
- `MEMBASE_ACCOUNT` - Ваш аккаунт для загрузки (0x...)
- `MEMBASE_CONVERSATION_ID` - ID вашего разговора, должен быть уникальным, предзагрузит его историю
- `MEMBASE_ID` - ID вашего экземпляра

## Примеры использования

```
Get conversation id and switch conversation
```

```
Save message and get messages
```

```
Call functions in llm chat
```

## Ресурсы

- [GitHub Repository](https://github.com/unibaseio/membase-mcp)

## Примечания

Сообщения или память можно просмотреть по адресу: https://testnet.hub.membase.io/. Сервер обеспечивает непрерывность работы агентов, персонализацию и отслеживаемость через децентрализованное хранение.