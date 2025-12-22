---
title: RAG Local MCP сервер
description: MCP сервер, который обеспечивает семантическое хранение и извлечение текста с использованием Ollama для создания эмбеддингов и ChromaDB для векторного хранения, позволяя вам запоминать и вспоминать текстовые фрагменты на основе смысла, а не ключевых слов.
tags:
- Vector Database
- AI
- Storage
- Search
- Database
author: renl
featured: false
---

MCP сервер, который обеспечивает семантическое хранение и извлечение текста с использованием Ollama для создания эмбеддингов и ChromaDB для векторного хранения, позволяя вам запоминать и вспоминать текстовые фрагменты на основе смысла, а не ключевых слов.

## Установка

### Из исходного кода

```bash
git clone <repository-url>
cd mcp-rag-local
curl -LsSf https://astral.sh/uv/install.sh | sh
docker-compose up
docker exec -it ollama ollama pull all-minilm:l6-v2
```

### Windows

```bash
git clone <repository-url>
cd mcp-rag-local
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
docker-compose up
docker exec -it ollama ollama pull all-minilm:l6-v2
```

## Конфигурация

### Конфигурация MCP сервера

```json
"mcp-rag-local": {
  "command": "uv",
  "args": [
    "--directory",
    "path\\to\\mcp-rag-local",
    "run",
    "main.py"
  ],
  "env": {
    "CHROMADB_PORT": "8321",
    "OLLAMA_PORT": "11434"
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `memorize_pdf_file` | Читает и запоминает содержимое PDF файлов, извлекая текст фрагментами по 20 страниц |
| `memorize_multiple_texts` | Сохраняет несколько текстовых фрагментов для семантического поиска |

## Возможности

- Семантическое хранение и извлечение текста на основе смысла, а не ключевых слов
- Обработка и запоминание PDF файлов по фрагментам
- Пакетное запоминание нескольких текстов
- Разбивка больших текстов на части для удобной работы
- Веб-интерфейс ChromaDB для управления памятью
- Использует Ollama для создания текстовых эмбеддингов и ChromaDB для векторного хранения

## Переменные окружения

### Опциональные
- `CHROMADB_PORT` - Порт для сервиса ChromaDB
- `OLLAMA_PORT` - Порт для сервиса Ollama

## Примеры использования

```
Memorize this text: "Singapore is an island country in Southeast Asia."
```

```
Memorize these texts: [list of texts]
```

```
Memorize this PDF file: C:\path\to\document.pdf
```

```
What is Singapore?
```

```
Please chunk the following long text and memorize all the chunks
```

## Ресурсы

- [GitHub Repository](https://github.com/renl/mcp-rag-local)

## Примечания

Включает веб-интерфейс администратора по адресу http://localhost:8322 для просмотра и управления содержимым векторной базы данных. Требует Docker для запуска сервисов ChromaDB и Ollama.