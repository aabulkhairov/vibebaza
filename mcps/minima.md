---
title: Minima MCP сервер
description: Open source RAG (Retrieval Augmented Generation) сервер, который предоставляет возможности поиска и индексации документов на локальных серверах, с поддержкой интеграции ChatGPT и полностью локальной работой.
tags:
- AI
- Search
- Vector Database
- Storage
- Integration
author: Community
featured: false
install_command: npx -y @smithery/cli install minima --client claude
---

Open source RAG (Retrieval Augmented Generation) сервер, который предоставляет возможности поиска и индексации документов на локальных серверах, с поддержкой интеграции ChatGPT и полностью локальной работой.

## Установка

### Docker - Полностью локально

```bash
docker compose -f docker-compose-ollama.yml --env-file .env up --build
```

### Docker - С поддержкой ChatGPT

```bash
docker compose -f docker-compose-chatgpt.yml --env-file .env up --build
```

### Docker - Интеграция MCP

```bash
docker compose -f docker-compose-mcp.yml --env-file .env up --build
```

### Smithery

```bash
npx -y @smithery/cli install minima --client claude
```

### Shell скрипт

```bash
./run.sh
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
      "minima": {
        "command": "uv",
        "args": [
          "--directory",
          "/path_to_cloned_minima_project/mcp-server",
          "run",
          "minima"
        ]
      }
    }
  }
```

### GitHub Copilot

```json
{
  "servers": {
    "minima": {
      "type": "stdio",
      "command": "path_to_cloned_minima_project/run_in_copilot.sh",
      "args": [
        "path_to_cloned_minima_project"
      ]
    }
  }
}
```

## Возможности

- Изолированная установка - полностью локально с контейнерами, без внешних зависимостей
- Интеграция с кастомными GPT - запросы к локальным документам через ChatGPT с пользовательскими GPT
- Интеграция с Anthropic Claude - использование приложения Claude для запросов к локальным документам
- Поддержка множества типов файлов: .pdf, .xls, .docx, .txt, .md, .csv
- Рекурсивная индексация документов в папках и подпапках
- Векторный поиск с использованием Qdrant хранилища
- Поддержка reranker моделей для улучшенной релевантности поиска
- Electron приложение для полностью локального использования

## Переменные окружения

### Обязательные
- `LOCAL_FILES_PATH` - Корневая папка для индексации документов (рекурсивный процесс)
- `EMBEDDING_MODEL_ID` - Модель Sentence Transformer для эмбеддингов
- `EMBEDDING_SIZE` - Размерность эмбеддингов для конфигурации векторного хранилища Qdrant

### Опциональные
- `OLLAMA_MODEL` - ID модели Ollama LLM для локального инференса
- `RERANKER_MODEL` - Reranker модель для улучшения релевантности поиска (протестированы BAAI модели)
- `USER_ID` - Email для аутентификации интеграции ChatGPT
- `PASSWORD` - Пароль для аутентификации интеграции ChatGPT

## Примеры использования

```
Задавайте любые вопросы, и вы получите ответы на основе локальных файлов в указанной папке
```

## Ресурсы

- [GitHub Repository](https://github.com/dmayboroda/minima)

## Примечания

Требует Python >=3.10 и установленный 'uv' для использования MCP. Chat UI доступен по адресу http://localhost:3000 для локального использования. Лицензия Mozilla Public License v2.0 (MPLv2).