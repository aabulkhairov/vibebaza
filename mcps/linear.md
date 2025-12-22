---
title: Linear MCP сервер
description: MCP сервер, который обеспечивает интеграцию с системой отслеживания задач Linear, позволяя LLM взаимодействовать с задачами Linear через поиск, создание, обновление и комментирование.
tags:
- Productivity
- API
- Integration
- DevOps
author: Community
featured: false
---

MCP сервер, который обеспечивает интеграцию с системой отслеживания задач Linear, позволяя LLM взаимодействовать с задачами Linear через поиск, создание, обновление и комментирование.

## Установка

### Smithery (Автоматически)

```bash
npx @smithery/cli install linear-mcp-server --client claude
```

### NPX (Вручную)

```bash
npx -y linear-mcp-server
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "linear": {
      "command": "npx",
      "args": [
        "-y",
        "linear-mcp-server"
      ],
      "env": {
        "LINEAR_API_KEY": "your_linear_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `linear_create_issue` | Создание новой задачи Linear с заголовком, ID команды и опциональными описанием, приоритетом и статусом |
| `linear_update_issue` | Обновление существующих задач с новым заголовком, описанием, приоритетом или статусом |
| `linear_search_issues` | Поиск задач с гибкой фильтрацией по запросу, команде, статусу, исполнителю, меткам, приоритету и лимиту |
| `linear_get_user_issues` | Получение задач, назначенных конкретному пользователю или аутентифицированному пользователю |
| `linear_add_comment` | Добавление комментариев к задачам с поддержкой markdown и опциональными пользователем/аватаром |

## Возможности

- Создание и обновление задач Linear
- Поиск задач с гибкими опциями фильтрации
- Просмотр деталей отдельных задач и задач команд
- Добавление комментариев к задачам с поддержкой markdown
- Доступ к задачам, назначенным пользователям, и информации об организации
- Доступ к данным Linear на основе ресурсов (задачи, команды, пользователи, организация)

## Переменные окружения

### Обязательные
- `LINEAR_API_KEY` - API ключ Linear для аутентификации вашей команды

## Примеры использования

```
Show me all my high-priority issues
```

```
Based on what I've told you about this bug already, make a bug report for the authentication system
```

```
Find all in progress frontend tasks
```

```
Give me a summary of recent updates on the issues for mobile app development
```

```
What's the current workload for the mobile team?
```

## Ресурсы

- [GitHub Repository](https://github.com/jerhadf/linear-mcp-server)

## Примечания

ВАЖНО: Этот MCP сервер устарел и больше не поддерживается. Вместо него рекомендуется использовать официальный удаленный MCP сервер Linear по адресу https://mcp.linear.app/sse