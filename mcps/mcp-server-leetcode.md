---
title: mcp-server-leetcode MCP сервер
description: Model Context Protocol (MCP) сервер для LeetCode, который позволяет AI-ассистентам получать доступ к задачам LeetCode, информации о пользователях и данным соревнований.
tags:
- Code
- API
- Productivity
- Analytics
author: doggybee
featured: false
---

Model Context Protocol (MCP) сервер для LeetCode, который позволяет AI-ассистентам получать доступ к задачам LeetCode, информации о пользователях и данным соревнований.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @doggybee/mcp-server-leetcode --client claude
```

### Глобальная установка

```bash
npm install -g @mcpfun/mcp-server-leetcode
mcp-server-leetcode
```

### Локальная установка

```bash
npm install @mcpfun/mcp-server-leetcode
```

### Из исходного кода

```bash
git clone https://github.com/doggybee/mcp-server-leetcode.git
cd mcp-server-leetcode
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "leetcode": {
      "command": "mcp-server-leetcode"
    }
  }
}
```

### Локальная разработка

```json
{
  "mcpServers": {
    "leetcode": {
      "command": "node",
      "args": ["/path/to/dist/index.js"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-daily-challenge` | Получить ежедневную задачу |
| `get-problem` | Получить детали конкретной задачи |
| `search-problems` | Поиск задач по критериям |
| `get-user-profile` | Получить информацию о пользователе |
| `get-user-submissions` | Получить историю отправок пользователя |
| `get-user-contest-ranking` | Получить рейтинги пользователя в соревнованиях |
| `get-contest-details` | Получить детали соревнования |

## Возможности

- Быстрый доступ к LeetCode API
- Поиск задач, получение ежедневных вызовов и проверка профилей пользователей
- Запрос данных и рейтингов соревнований
- Полная поддержка MCP инструментов и ресурсов
- Предоставляет как CLI, так и программируемый API

## Ресурсы

- [GitHub Repository](https://github.com/doggybee/mcp-server-leetcode)

## Примечания

Сервер предоставляет как инструменты для доступа к данным LeetCode, так и ресурсы, используя URI-паттерны вроде leetcode://daily-challenge и leetcode://problem/{titleSlug}. Также может использоваться как JavaScript-библиотека с классом LeetCodeService.