---
title: mac-messages-mcp сервер
description: Python-мост для взаимодействия с приложением Сообщения macOS через MCP, обеспечивающий универсальную отправку сообщений через iMessage или SMS/RCS с умными возможностями резервного подключения.
tags:
- Messaging
- API
- Integration
- Productivity
author: Community
featured: false
---

Python-мост для взаимодействия с приложением Сообщения macOS через MCP, обеспечивающий универсальную отправку сообщений через iMessage или SMS/RCS с умными возможностями резервного подключения.

## Установка

### PyPI

```bash
uv pip install mac-messages-mcp
```

### Из исходного кода

```bash
git clone https://github.com/carterlasalle/mac_messages_mcp.git
cd mac_messages_mcp
uv install -e .
```

### UVX

```bash
uvx mac-messages-mcp
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "messages": {
            "command": "uvx",
            "args": [
                "mac-messages-mcp"
            ]
        }
    }
}
```

### Cursor

```json
uvx mac-messages-mcp
```

## Возможности

- Универсальная отправка сообщений - Автоматически отправляет через iMessage или SMS/RCS в зависимости от доступности получателя
- Умное резервное подключение - Плавный переход на SMS, когда iMessage недоступен (идеально для пользователей Android)
- Чтение сообщений - Чтение недавних сообщений из приложения Сообщения macOS
- Фильтрация контактов - Фильтрация сообщений по конкретным контактам или номерам телефонов
- Нечёткий поиск - Поиск по содержимому сообщений с интеллектуальным сопоставлением
- Определение iMessage - Проверка наличия iMessage у получателей перед отправкой
- Кроссплатформенность - Работает как с пользователями iPhone/Mac (iMessage), так и с пользователями Android (SMS/RCS)

## Примеры использования

```
Send to iPhone user via iMessage
```

```
Send to Android user automatically via SMS
```

```
Check delivery method before sending
```

```
Get recent messages from the past 48 hours
```

```
Send messages to mixed groups with optimal delivery method
```

## Ресурсы

- [GitHub Repository](https://github.com/carterlasalle/mac_messages_mcp)

## Примечания

Требует macOS 11+, Python 3.10+, менеджер пакетов uv, и разрешение Full Disk Access для терминала/приложения для доступа к базе данных Сообщений. Запускайте только один экземпляр (либо в Cursor, либо в Claude Desktop). Включает интеграцию с Docker-контейнером через mcp-proxy.