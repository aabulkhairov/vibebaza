---
title: cognee-mcp сервер
description: GraphRAG сервер памяти, который запускает движок памяти cognee как MCP сервер,
  предоставляя AI агентам возможности постоянной памяти через хранение и поиск в графе знаний.
tags:
- AI
- Database
- Vector Database
- Search
- Analytics
author: Community
featured: false
install_command: claude mcp add cognee-sse -t sse http://localhost:8000/sse
---

GraphRAG сервер памяти, который запускает движок памяти cognee как MCP сервер, предоставляя AI агентам возможности постоянной памяти через хранение и поиск в графе знаний.

## Установка

### Из исходного кода

```bash
git clone https://github.com/topoteretes/cognee.git
cd cognee/cognee-mcp
pip install uv
uv sync --dev --all-extras --reinstall
source .venv/bin/activate
python src/server.py
```

### Сборка Docker

```bash
docker rmi cognee/cognee-mcp:main || true
docker build --no-cache -f cognee-mcp/Dockerfile -t cognee/cognee-mcp:main .
docker run -e TRANSPORT_MODE=http --env-file ./.env -p 8000:8000 --rm -it cognee/cognee-mcp:main
```

### Docker Hub

```bash
docker run -e TRANSPORT_MODE=http --env-file ./.env -p 8000:8000 --rm -it cognee/cognee-mcp:main
```

## Конфигурация

### Claude Desktop SSE

```json
{
  "mcpServers": {
    "cognee": {
      "type": "sse",
      "url": "http://localhost:8000/sse"
    }
  }
}
```

### Claude Desktop HTTP

```json
{
  "mcpServers": {
    "cognee": {
      "type": "http",
      "url": "http://localhost:8000/mcp"
    }
  }
}
```

### Cursor SSE

```json
{
  "mcpServers": {
    "cognee-sse": {
      "url": "http://localhost:8000/sse"
    }
  }
}
```

### Cursor HTTP

```json
{
  "mcpServers": {
    "cognee-http": {
      "url": "http://localhost:8000/mcp"
    }
  }
}
```

## Возможности

- Множественные транспорты – выбирайте между потоковым HTTP, SSE (потоковая передача в реальном времени), или stdio
- Режим API – подключение к уже запущенному серверу Cognee FastAPI вместо прямого использования cognee
- Интегрированное логирование – все действия записываются в ротируемый файл и дублируются в консоль
- Локальный импорт файлов – загружайте .md файлы, исходный код, наборы правил Cursor и другие файлы прямо с диска
- Фоновые пайплайны – долгоработающие задачи cognify и codify выполняются в отдельном потоке
- Загрузка правил разработчика – индексирует .cursorrules, .cursor/rules, AGENT.md в узел developer_rules
- Очистка и сброс – полная очистка памяти одним вызовом prune

## Переменные окружения

### Обязательные
- `LLM_API_KEY` - OpenAI API ключ для конфигурации по умолчанию

### Опциональные
- `TRANSPORT_MODE` - Режим транспорта для Docker (http, sse, stdio)
- `EXTRAS` - Дополнительные группы зависимостей для установки во время выполнения (через запятую)
- `API_URL` - Базовый URL запущенного сервера Cognee FastAPI для режима API
- `API_TOKEN` - Токен аутентификации для режима API

## Ресурсы

- [GitHub Repository](https://github.com/topoteretes/cognee)

## Примечания

Поддерживает множество опциональных групп зависимостей, включая AWS, PostgreSQL, Neo4j, ChromaDB и другие. Может работать в прямом режиме (по умолчанию) или в режиме API для подключения к существующим серверам Cognee. Режим API имеет некоторые ограничения, включая отсутствие codify, отслеживания статуса пайплайнов или возможностей очистки.