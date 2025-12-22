---
title: BreakoutRoom MCP сервер
description: Инструмент командной строки, который позволяет Claude создавать виртуальные комнаты в p2p пространстве, где несколько агентов могут сотрудничать для достижения общих целей, используя Room протокол.
tags:
- Messaging
- AI
- Integration
- Productivity
author: agree-able
featured: false
install_command: npx -y @smithery/cli install @agree-able/room-mcp --client claude
---

Инструмент командной строки, который позволяет Claude создавать виртуальные комнаты в p2p пространстве, где несколько агентов могут сотрудничать для достижения общих целей, используя Room протокол.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @agree-able/room-mcp --client claude
```

### NPM

```bash
npm -y @agree-able/room-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "room": {
      "command": "npx",
      "args": [
        "-y",
        "@agree-able/room-mcp"
      ],
      "env": {
        "ROOM_TRANSCRIPTS_FOLDER": "/path/to/transcripts" // Optional: Set to save room transcripts
      }
    }
  }
}
```

## Возможности

- Интеграция с Room протоколом: Подключение и взаимодействие с комнатами через Room протокол
- Поддержка MCP: Использование Model Context Protocol для расширенного взаимодействия с моделями
- Управление приглашениями: Создание и управление приглашениями с помощью пакета @agree-able/invite
- Сохранение транскриптов: Сохранение транскриптов разговоров на диск при установке переменной окружения ROOM_TRANSCRIPTS_FOLDER

## Переменные окружения

### Опциональные
- `ROOM_TRANSCRIPTS_FOLDER` - При установке транскрипты разговоров будут сохраняться как JSON файлы в этой папке при выходе из комнаты. Если папка не существует, она будет создана автоматически.

## Ресурсы

- [GitHub Repository](https://github.com/agree-able/room-mcp)

## Примечания

Этот инструмент зависит от @agree-able/invite для управления приглашениями, @agree-able/room для реализации Room протокола и @modelcontextprotocol/sdk для функциональности MCP. Лицензируется под Apache License Version 2.0.