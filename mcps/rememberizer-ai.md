---
title: Rememberizer AI MCP сервер
description: MCP сервер, который позволяет большим языковым моделям искать, извлекать и управлять документами и знаниями через API управления документами и знаниями Rememberizer.
tags:
- AI
- Search
- Productivity
- Integration
- API
author: skydeckai
featured: false
---

MCP сервер, который позволяет большим языковым моделям искать, извлекать и управлять документами и знаниями через API управления документами и знаниями Rememberizer.

## Установка

### Ручная установка

```bash
uvx mcp-server-rememberizer
```

### Через приложение MseeP AI Helper

```bash
Search for "Rememberizer" and install the mcp-server-rememberizer
```

## Конфигурация

### Claude Desktop

```json
"mcpServers": {
  "rememberizer": {
      "command": "uvx",
      "args": ["mcp-server-rememberizer"],
      "env": {
        "REMEMBERIZER_API_TOKEN": "your_rememberizer_api_token"
      }
    },
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `retrieve_semantically_similar_internal_knowledge` | Отправляет блок текста и получает семантически похожие совпадения из вашей подключенной персоны Rememberizer... |
| `smart_search_internal_knowledge` | Ищет документы в Rememberizer, используя простой запрос, который возвращает результаты агентного поиска... |
| `list_internal_knowledge_systems` | Перечисляет источники личных/командных внутренних знаний, включая обсуждения Slack, Gmail, Dropbox... |
| `rememberizer_account_information` | Получает информацию о вашем аккаунте репозитория личных/командных знаний Rememberizer.ai, включая... |
| `list_personal_team_knowledge_documents` | Извлекает постраничный список всех документов в вашей системе личных/командных знаний из различных источников... |
| `remember_this` | Сохраняет текстовую информацию в вашей системе знаний Rememberizer.ai для будущего извлечения... |

## Возможности

- Семантический поиск по сходству в репозиториях личных/командных знаний
- Интеграция с множественными источниками данных (Slack, Gmail, Dropbox, Google Drive)
- Возможности управления и извлечения документов
- Хранение памяти для будущего воспроизведения знаний
- Функциональность поиска с фильтрацией по дате
- Постраничный список документов
- Доступ к информации аккаунта

## Переменные окружения

### Обязательные
- `REMEMBERIZER_API_TOKEN` - Ваш API токен Rememberizer для аутентификации

## Примеры использования

```
What is my Rememberizer account?
```

```
List all documents that I have there.
```

```
Give me a quick summary about "..."
```

## Ресурсы

- [GitHub Repository](https://github.com/skydeckai/mcp-server-rememberizer)

## Примечания

Сервер находится в разработке, и функциональность может изменяться. Вы можете зарегистрировать API ключ, создав собственную Common Knowledge в Rememberizer. Предоставляемые ресурсы включают документы и обсуждения Slack.