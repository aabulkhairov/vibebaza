---
title: Webex MCP сервер
description: Model Context Protocol (MCP) сервер, который предоставляет AI-ассистентам полный доступ к возможностям Cisco Webex мессенджера через 52 различных инструмента, охватывающих сообщения, комнаты, команды, людей, webhooks и корпоративные функции.
tags:
- Messaging
- Integration
- API
- Productivity
author: Community
featured: false
---

Model Context Protocol (MCP) сервер, который предоставляет AI-ассистентам полный доступ к возможностям Cisco Webex мессенджера через 52 различных инструмента, охватывающих сообщения, комнаты, команды, людей, webhooks и корпоративные функции.

## Установка

### Из исходников

```bash
git clone <repository-url>
cd webex-messaging-mcp-server
npm install
```

### Docker

```bash
docker build -t webex-mcp-server .
docker run -i --rm --env-file .env webex-mcp-server
```

### Docker Compose

```bash
docker-compose up webex-mcp-server
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "webex-messaging": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "WEBEX_PUBLIC_WORKSPACE_API_KEY",
        "-e",
        "WEBEX_USER_EMAIL",
        "-e",
        "WEBEX_API_BASE_URL",
        "webex-mcp-server"
      ],
      "env": {
        "WEBEX_USER_EMAIL": "your.email@company.com",
        "WEBEX_API_BASE_URL": "https://webexapis.com/v1",
        "WEBEX_PUBLIC_WORKSPACE_API_KEY": "your_token_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `create_message` | Отправка сообщений в комнаты |
| `list_messages` | Получение истории сообщений |
| `edit_message` | Изменение существующих сообщений |
| `delete_message` | Удаление сообщений |
| `get_message_details` | Получение информации о конкретном сообщении |
| `create_room` | Создание новых пространств Webex |
| `list_rooms` | Просмотр доступных комнат |
| `get_room_details` | Получение информации о комнате |
| `update_room` | Изменение настроек комнаты |
| `delete_room` | Удаление комнат |
| `create_team` | Создание команд |
| `list_teams` | Просмотр команд |
| `get_team_details` | Получение информации о команде |
| `update_team` | Изменение настроек команды |
| `delete_team` | Удаление команд |

## Возможности

- Полное покрытие Webex API: 52 инструмента, охватывающих все основные операции мессенджера
- Поддержка Docker: Готовая к продакшену контейнеризация
- Двойной транспорт: Режимы STDIO и HTTP (StreamableHTTP)
- Готов к корпоративному использованию: Поддерживает корпоративную аутентификацию Cisco
- Type Safe: Полная реализация на TypeScript/JavaScript с правильной обработкой ошибок
- Централизованная конфигурация: Простое управление токенами и эндпоинтами

## Переменные окружения

### Обязательные
- `WEBEX_PUBLIC_WORKSPACE_API_KEY` - токен Webex API (без префикса 'Bearer ')

### Опциональные
- `WEBEX_API_BASE_URL` - базовый URL Webex API
- `WEBEX_USER_EMAIL` - ваш email в Webex (для справки)
- `PORT` - порт для HTTP режима
- `MCP_MODE` - режим транспорта (stdio или http)

## Ресурсы

- [GitHub Repository](https://github.com/Kashyap-AI-ML-Solutions/webex-messaging-mcp-server)

## Примечания

Webex Bearer токены действуют недолго (12 часов) и требуют регулярного обновления с developer.webex.com. Сервер поддерживает полное обнаружение инструментов со 118 юнит-тестами и 100% успешным прохождением. Включает предкоммитные проверки качества и поддерживает транспортные режимы STDIO и HTTP для различных MCP клиентов.