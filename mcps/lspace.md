---
title: Lspace MCP сервер
description: Open-source API бэкенд и MCP сервер, который захватывает инсайты из AI сессий и мгновенно делает их доступными через различные инструменты, превращая разрозненные разговоры в постоянные, поисковые базы знаний.
tags:
- AI
- Storage
- Productivity
- Integration
- Database
author: Community
featured: false
---

Open-source API бэкенд и MCP сервер, который захватывает инсайты из AI сессий и мгновенно делает их доступными через различные инструменты, превращая разрозненные разговоры в постоянные, поисковые базы знаний.

## Установка

### Из исходного кода

```bash
git clone https://github.com/Lspace-io/lspace-server.git
cd lspace-server
npm install
npm run build
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "lspace-knowledge-base": {
      "command": "node",
      "args": ["/actual/absolute/path/to/your/lspace-server/lspace-mcp-server.js"],
      "env": {
        // .env file in lspace-server directory should be picked up automatically.
        // Only add environment variables here if you need to override them
        // specifically for Cursor, or if the .env file is not found.
        // "OPENAI_API_KEY": "your_openai_key_if_not_in_lspace_env"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "lspace": {
      "command": "node",
      "args": ["/actual/absolute/path/to/your/lspace-server/lspace-mcp-server.js"]
      // "env": { ... } // Similar environment variable considerations as with Cursor
    }
  }
}
```

## Возможности

- Самостоятельно размещаемый сервис для git операций, поиска и LLM интеграции
- Мультирепозиторное управление с поддержкой множественных git провайдеров (локальный, GitHub)
- AI оркестрация для автоматической классификации документов, организации и суммаризации
- Генерация базы знаний для создания Wikipedia-подобного синтеза содержимого репозитория
- Репозитории с двойной структурой с необработанными документами и синтезированной базой знаний
- Отслеживание временной шкалы для операций с документами
- Расширяемая архитектура для кастомных интеграций

## Переменные окружения

### Обязательные
- `OPENAI_API_KEY` - OpenAI API ключ для LLM интеграции

## Ресурсы

- [GitHub Repository](https://github.com/Lspace-io/lspace-server)

## Примечания

Требует конфигурации config.local.json с деталями репозитория и GitHub Personal Access токенами для доступа к репозиторию. Использует репозитории с двойной структурой с хранением необработанных документов в /.lspace/raw_inputs/ и синтезом базы знаний в корне репозитория. Лицензирован под Business Source License 1.1 с автоматическим преобразованием в Apache License 2.0 через год.