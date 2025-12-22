---
title: eBook MCP сервер
description: Мощный сервер Model Context Protocol для обработки электронных книг
  (EPUB и PDF), который обеспечивает естественное общение с вашей цифровой библиотекой
  через взаимодействие на основе ИИ.
tags:
- AI
- Productivity
- Media
- Integration
- Storage
author: Community
featured: false
---

Мощный сервер Model Context Protocol для обработки электронных книг (EPUB и PDF), который обеспечивает естественное общение с вашей цифровой библиотекой через взаимодействие на основе ИИ.

## Установка

### Из исходного кода

```bash
git clone https://github.com/yourusername/ebook-mcp.git
cd ebook-mcp
uv pip install -e .
```

## Конфигурация

### Cursor

```json
"ebook-mcp":{
    "command": "uv",
    "args": [
        "--directory",
        "/Users/onebird/github/ebook-mcp/src/ebook_mcp/",
        "run",
        "main.py"
    ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_all_epub_files` | Получить все EPUB файлы в указанной директории |
| `get_metadata` | Извлечь метаданные из EPUB файлов (название, автор, дата публикации и т.д.) |
| `get_toc` | Получить содержание из EPUB файлов |
| `get_chapter_markdown` | Получить содержимое главы в формате Markdown из EPUB файлов |
| `get_all_pdf_files` | Получить все PDF файлы в указанной директории |
| `get_pdf_metadata` | Извлечь метаданные из PDF файлов |
| `get_pdf_toc` | Получить содержание из PDF файлов |
| `get_pdf_page_text` | Получить текстовое содержимое с конкретных страниц PDF |
| `get_pdf_page_markdown` | Получить содержимое в формате Markdown с конкретных страниц PDF |
| `get_pdf_chapter_content` | Получить содержимое главы и соответствующие номера страниц по названию главы |

## Возможности

- Умное управление библиотекой - поиск книг по формату или теме
- Интерактивный опыт чтения - беседы о содержании книг
- Поддержка активного обучения - создание викторин и упражнений на основе книг
- Навигация по контенту - поиск разделов с помощью запросов на естественном языке
- Поддержка форматов EPUB и PDF
- Извлечение метаданных (название, автор, даты)
- Извлечение содержания
- Извлечение содержимого глав с выводом в Markdown
- Возможности пакетной обработки

## Примеры использования

```
Show me all EPUB files in my downloads folder
```

```
Find books about GenAI in my library
```

```
Give me a brief introduction to 'LLM Engineer Handbook'
```

```
What's covered in Chapter 3?
```

```
Summarize the key points about RAG from this book
```

## Ресурсы

- [GitHub Repository](https://github.com/onebirdrocks/ebook-mcp)

## Примечания

Обработка PDF опирается на содержание документа - некоторые функции могут не работать, если содержание недоступно. Для больших PDF файлов рекомендуется обрабатывать по диапазонам страниц. ID глав EPUB должны быть получены из структуры содержания. Доступен на нескольких языках: английский, китайский, японский, корейский, французский и немецкий.