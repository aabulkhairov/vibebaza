---
title: Langflow-DOC-QA-SERVER MCP сервер
description: MCP сервер для работы с документами в режиме вопрос-ответ на базе Langflow.
  Предоставляет простой интерфейс для запросов к документам через бэкенд Langflow.
tags:
- AI
- Integration
- API
- Productivity
author: GongRzhe
featured: false
---

MCP сервер для работы с документами в режиме вопрос-ответ на базе Langflow. Предоставляет простой интерфейс для запросов к документам через бэкенд Langflow.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @GongRzhe/Langflow-DOC-QA-SERVER --client claude
```

### Из исходного кода

```bash
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "langflow-doc-qa-server": {
      "command": "node",
      "args": [
        "/path/to/doc-qa-server/build/index.js"
      ],
      "env": {
        "API_ENDPOINT": "http://127.0.0.1:7860/api/v1/run/480ec7b3-29d2-4caa-b03b-e74118f35fac"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `query_docs` | Выполняет запрос к системе вопрос-ответ по документам с помощью строки запроса и возвращает ответы от бэкенда Langflow |

## Возможности

- Система вопрос-ответ по документам на базе Langflow
- MCP сервер на TypeScript
- Простой интерфейс для запросов к документам
- Интеграция с бэкенд API Langflow

## Переменные окружения

### Опциональные
- `API_ENDPOINT` - URL эндпоинта для сервиса Langflow API

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/Langflow-DOC-QA-SERVER)

## Примечания

Требует предварительной настройки Langflow Document Q&A Flow. Сервер включает поддержку отладки через MCP Inspector (npm run inspector). Доступен режим разработки с автоматической пересборкой (npm run watch).