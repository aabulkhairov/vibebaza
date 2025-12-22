---
title: memos-api-mcp сервер
description: Реализация Model Context Protocol для API сервиса MemOS, которая предоставляет возможности управления памятью разговоров и обработки сообщений для AI приложений.
tags:
- AI
- API
- Storage
- Messaging
- Analytics
author: Community
featured: false
---

Реализация Model Context Protocol для API сервиса MemOS, которая предоставляет возможности управления памятью разговоров и обработки сообщений для AI приложений.

## Установка

### NPM Global

```bash
npm install -g @memtensor/memos-api-mcp
```

### PNPM Global

```bash
pnpm add -g @memtensor/memos-api-mcp
```

### NPX Direct

```bash
npx @memtensor/memos-api-mcp
```

## Конфигурация

### MCP Client

```json
{
  "mcpServers": {
    "memos-api-mcp": {
      "command": "npx",
      "args": ["-y", "@memtensor/memos-api-mcp"],
      "env": {
        "MEMOS_API_KEY": "your-api-key",
        "MEMOS_USER_ID": "your-user-id",
        "MEMOS_CHANNEL": "the-site-where-you-are-seeing-this-document"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `add_message` | Добавляет новое сообщение в разговор с информацией о роли и содержимом |
| `search_memory` | Ищет воспоминания в разговоре, используя текстовый запрос с настраиваемыми лимитами результатов |
| `get_message` | Получает сообщения из определенного разговора |

## Возможности

- MCP-совместимый API интерфейс
- Инструмент командной строки для удобного взаимодействия
- Построен на TypeScript для безопасности типов
- Реализация сервера на Express.js
- Валидация схем с помощью Zod

## Переменные окружения

### Обязательные
- `MEMOS_API_KEY` - Ваш API ключ Memos для аутентификации
- `MEMOS_USER_ID` - Стабильный идентификатор для пользователя, который является детерминированным и не содержит персональных данных, должен оставаться одинаковым на всех устройствах/сессиях
- `MEMOS_CHANNEL` - Сайт, где вы видите этот документ (например, MODELSCOPE, MCPSO, GITHUB и т.д.)

## Ресурсы

- [GitHub Repository](https://github.com/MemTensor/memos-api-mcp)

## Примечания

Требует Node.js >= 18. Текущая версия 1.0.0-beta.2. MEMOS_USER_ID должен быть сгенерирован с помощью SHA-256(lowercase(trim(email))) или SSO subject/employee ID - никогда не используйте случайные значения или идентификаторы устройств.