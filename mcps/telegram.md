---
title: Telegram MCP сервер
description: Комплексная интеграция с Telegram для MCP-совместимых клиентов, которая предоставляет полный доступ к функциональности Telegram, включая обмен сообщениями, управление чатами, управление контактами и администрирование групп через Telethon.
tags:
- Messaging
- Integration
- API
- Productivity
- AI
author: chigwell
featured: true
---

Комплексная интеграция с Telegram для MCP-совместимых клиентов, которая предоставляет полный доступ к функциональности Telegram, включая обмен сообщениями, управление чатами, управление контактами и администрирование групп через Telethon.

## Установка

### Из исходного кода

```bash
git clone https://github.com/chigwell/telegram-mcp.git
cd telegram-mcp
uv sync
```

### Сборка Docker

```bash
docker build -t telegram-mcp:latest .
```

### Docker Compose

```bash
docker compose up --build
```

### Запуск Docker

```bash
docker run -it --rm \
  -e TELEGRAM_API_ID="YOUR_API_ID" \
  -e TELEGRAM_API_HASH="YOUR_API_HASH" \
  -e TELEGRAM_SESSION_STRING="YOUR_SESSION_STRING" \
  telegram-mcp:latest
```

## Конфигурация

### Claude Desktop / Cursor

```json
{
  "mcpServers": {
    "telegram-mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "/full/path/to/telegram-mcp",
        "run",
        "main.py"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_chats` | Получить постраничный список чатов |
| `list_chats` | Список чатов с метаданными и фильтрацией |
| `get_chat` | Получить подробную информацию о чате |
| `send_message` | Отправить сообщение в определенный чат |
| `get_messages` | Получить постраничные сообщения из чата |
| `reply_to_message` | Ответить на конкретное сообщение |
| `edit_message` | Редактировать собственное сообщение |
| `delete_message` | Удалить сообщение |
| `forward_message` | Переслать сообщение между чатами |
| `create_group` | Создать новую группу |
| `create_channel` | Создать канал или супергруппу |
| `get_participants` | Список всех участников чата |
| `promote_admin` | Повысить пользователя до админа |
| `ban_user` | Заблокировать пользователя в чате |
| `list_contacts` | Список всех контактов |

## Возможности

- Полные возможности управления чатами и группами
- Комплексные инструменты для сообщений, включая редактирование, пересылку и ответы
- Управление контактами и блокировка/разблокировка пользователей
- Функции администратора, такие как повышение/понижение пользователей и управление блокировками
- Создание и управление каналами и супергруппами
- Взаимодействие с inline-клавиатурой и нажатие кнопок
- Создание опросов и закрепление сообщений
- Функциональность поиска публичных чатов и сообщений
- Управление настройками приватности
- Получение информации о медиафайлах

## Переменные окружения

### Обязательные
- `TELEGRAM_API_ID` - Ваш Telegram API ID с my.telegram.org/apps
- `TELEGRAM_API_HASH` - Ваш Telegram API Hash с my.telegram.org/apps
- `TELEGRAM_SESSION_STRING` - Строка сессии, сгенерированная session_string_generator.py

### Опциональные
- `TELEGRAM_SESSION_NAME` - Альтернатива строке сессии для файловых сессий

## Примеры использования

```
Analyze my chat history and send a response to the group
```

```
Get my recent messages from a specific chat
```

```
Send a message to my project group
```

```
Create a new group with specific users
```

```
List all my contacts and find someone
```

## Ресурсы

- [GitHub Repository](https://github.com/chigwell/telegram-mcp)

## Примечания

Требует Python 3.10+. Вам необходимо сгенерировать учетные данные API на my.telegram.org/apps и создать строку сессии, используя прилагаемый скрипт-генератор. Файловые операции (отправка файлов, загрузка медиа) были удалены из-за ограничений среды MCP. Сервер предоставляет валидацию входных данных, принимая целочисленные ID, строковые ID или имена пользователей для параметров чата/пользователя.