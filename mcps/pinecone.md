---
title: Pinecone MCP сервер
description: MCP сервер для чтения и записи в векторные базы данных Pinecone, который
  обеспечивает семантический поиск и обработку документов с RAG возможностями, используя
  Pinecone Inference API.
tags:
- Vector Database
- AI
- Search
- Storage
- Integration
author: Community
featured: false
---

MCP сервер для чтения и записи в векторные базы данных Pinecone, который обеспечивает семантический поиск и обработку документов с RAG возможностями, используя Pinecone Inference API.

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp-pinecone --client claude
```

### UV (рекомендуется)

```bash
uvx install mcp-pinecone
```

### UV pip

```bash
uv pip install mcp-pinecone
```

## Конфигурация

### Claude Desktop (разработка)

```json
{
  "mcpServers": {
    "mcp-pinecone": {
      "command": "uv",
      "args": [
        "--directory",
        "{project_dir}",
        "run",
        "mcp-pinecone"
      ]
    }
  }
}
```

### Claude Desktop (опубликованная версия)

```json
{
  "mcpServers": {
    "mcp-pinecone": {
      "command": "uvx",
      "args": [
        "--index-name",
        "{your-index-name}",
        "--api-key",
        "{your-secret-api-key}",
        "mcp-pinecone"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `semantic-search` | Поиск записей в индексе Pinecone |
| `read-document` | Чтение документа из индекса Pinecone |
| `list-documents` | Список всех документов в индексе Pinecone |
| `pinecone-stats` | Получение статистики индекса Pinecone, включая количество записей, размерности и пространства имен |
| `process-document` | Обработка документа на фрагменты и их загрузка в индекс Pinecone. Выполняет общую... |

## Возможности

- Чтение и запись в индекс Pinecone
- Возможности семантического поиска
- Обработка документов с разделением на токены
- Автоматическая генерация эмбеддингов через Pinecone inference API
- Статистика и мониторинг векторной базы данных
- Список документов и их получение

## Ресурсы

- [GitHub Repository](https://github.com/sirmews/mcp-pinecone)

## Примечания

Требует аккаунт Pinecone и API ключ. Создайте индекс в панели Pinecone и получите учетные данные API. Эмбеддинги генерируются через Pinecone inference API, а разбиение на фрагменты выполняется с помощью токенного разделителя. Лучше всего отлаживается с помощью MCP Inspector.