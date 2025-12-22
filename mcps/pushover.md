---
title: Pushover MCP сервер
description: Реализация Model Context Protocol для отправки уведомлений через Pushover.net, позволяющая AI агентам отправлять мгновенные уведомления на устройства.
tags:
- Messaging
- Integration
- Productivity
- API
author: Community
featured: false
---

Реализация Model Context Protocol для отправки уведомлений через Pushover.net, позволяющая AI агентам отправлять мгновенные уведомления на устройства.

## Установка

### NPX Global

```bash
npx -y pushover-mcp@latest start --token YOUR_TOKEN --user YOUR_USER
```

### Smithery

```bash
npx -y @smithery/cli install @AshikNesin/pushover-mcp --client claude
```

### Из исходного кода

```bash
pnpm install
pnpm build
```

## Конфигурация

### Cursor Project

```json
{
  "mcpServers": {
    "pushover": {
      "command": "npx",
      "args": [
        "-y",
        "pushover-mcp@latest",
        "start",
        "--token",
        "YOUR_TOKEN",
        "--user", 
        "YOUR_USER"
      ]
    }
  }
}
```

### Roo Code

```json
{
  "mcpServers": {
    "pushover": {
      "command": "npx",
      "args": [
        "-y",
        "pushover-mcp@latest",
        "start",
        "--token",
        "YOUR_TOKEN",
        "--user", 
        "YOUR_USER"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `send` | Отправляет уведомление через Pushover с настраиваемым сообщением, заголовком, приоритетом, звуком, URL и уст... |

## Возможности

- Отправка уведомлений через Pushover.net
- Настраиваемые заголовки и содержимое сообщений
- Уровни приоритета от -2 (минимальный) до 2 (экстренный)
- Пользовательские звуки уведомлений
- Включение URL с пользовательскими заголовками
- Отправка на конкретные устройства
- Соответствие спецификации MCP для интеграции с AI системами

## Примеры использования

```
Send a notification with title and priority
```

```
Send an emergency notification
```

```
Include a URL in the notification
```

```
Target a specific device for the notification
```

## Ресурсы

- [GitHub Repository](https://github.com/ashiknesin/pushover-mcp)

## Примечания

Требует токен приложения Pushover.net и пользовательский ключ из панели управления. Совместим с Cursor IDE и Roo Code. Агент будет запрашивать подтверждение перед отправкой уведомлений, если не включен режим 'Yolo mode'.