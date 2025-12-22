---
title: MCP Documentation Server MCP сервер
description: TypeScript-based MCP сервер для локального управления документами
  и семантического поиска с использованием эмбеддингов или Google Gemini AI, с персистентностью на диске,
  индексированием в памяти и кэшированием для оптимизации производительности.
tags:
- AI
- Search
- Storage
- Analytics
- Productivity
author: andrea9293
featured: true
---

TypeScript-based MCP сервер, который обеспечивает локальное управление документами и семантический поиск с использованием эмбеддингов или Google Gemini AI, с персистентностью на диске, индексированием в памяти и кэшированием для оптимизации производительности.

## Установка

### NPX

```bash
npx -y @andrea9293/mcp-documentation-server
```

### Из исходников

```bash
git clone https://github.com/andrea9293/mcp-documentation-server.git
cd mcp-documentation-server
npm run dev
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "documentation": {
      "command": "npx",
      "args": [
        "-y",
        "@andrea9293/mcp-documentation-server"
      ],
      "env": {
            "GEMINI_API_KEY": "your-api-key-here",  // Optional, enables AI-powered search
            "MCP_EMBEDDING_MODEL": "Xenova/all-MiniLM-L6-v2",
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `add_document` | Добавить документ (заголовок, содержимое, метаданные) |
| `list_documents` | Показать список сохраненных документов и метаданных |
| `get_document` | Получить полный документ по id |
| `delete_document` | Удалить документ, его части и связанные исходные файлы |
| `process_uploads` | Преобразовать файлы в папке uploads в документы (разбивка на части + эмбеддинги + сохранение резервных копий) |
| `get_uploads_path` | Возвращает абсолютный путь к папке uploads |
| `list_uploads_files` | Показывает файлы в папке uploads |
| `search_documents_with_ai` | AI-поиск с использованием Gemini для продвинутого анализа документов (требует GEMINI_API_KEY) |
| `search_documents` | Семантический поиск внутри документа (возвращает найденные части и подсказку LLM) |
| `get_context_window` | Вернуть окно частей документа вокруг целевого индекса части |

## Возможности

- AI-поиск с Google Gemini для контекстного понимания и интеллектуальной аналитики
- Традиционный семантический поиск с использованием эмбеддингов и индекса ключевых слов в памяти
- O(1) поиск документов и индекс ключевых слов для мгновенного получения данных
- LRU кэш эмбеддингов для избежания повторных вычислений
- Параллельная разбивка на части и пакетная обработка для больших документов
- Потоковое чтение файлов для обработки больших файлов без высокого потребления памяти
- Интеллектуальная обработка файлов с копированием и автоматическим сохранением резервных копий
- Локальное хранение без внешней базы данных
- Получение контекстного окна для более богатых ответов LLM
- Кэш сопоставления файлов для избежания повторной загрузки одинаковых файлов в Gemini

## Переменные окружения

### Опциональные
- `GEMINI_API_KEY` - API ключ Google Gemini для функций AI-поиска
- `MCP_EMBEDDING_MODEL` - Название модели эмбеддингов (по умолчанию: Xenova/all-MiniLM-L6-v2)
- `MCP_INDEXING_ENABLED` - Включить/отключить DocumentIndex (по умолчанию: true)
- `MCP_CACHE_SIZE` - Размер LRU кэша эмбеддингов (по умолчанию: 1000)
- `MCP_PARALLEL_ENABLED` - Включить параллельную разбивку на части (по умолчанию: true)
- `MCP_MAX_WORKERS` - Количество параллельных воркеров для разбивки/индексирования (по умолчанию: 4)
- `MCP_STREAMING_ENABLED` - Включить потоковое чтение для больших файлов (по умолчанию: true)
- `MCP_STREAM_CHUNK_SIZE` - Размер буфера потока в байтах (по умолчанию: 65536)

## Примеры использования

```
Search for 'variable assignment' in a document
```

```
Explain the main concepts and their relationships in a document
```

```
What are the key architectural patterns and how do they work together?
```

```
Summarize the core principles and provide examples
```

```
Compare these different approaches
```

## Ресурсы

- [GitHub Repository](https://github.com/andrea9293/mcp-documentation-server)

## Примечания

Поддерживает файлы .txt, .md и .pdf. Данные хранятся локально в ~/.mcp-documentation-server/. Изменение моделей эмбеддингов требует повторного добавления всех документов. Построен с FastMCP и TypeScript. Модели эмбеддингов загружаются при первом использовании и могут требовать несколько сотен MB.