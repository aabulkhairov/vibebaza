---
title: Markdownify MCP сервер
description: MCP сервер для преобразования различных типов файлов (PDF, изображения, аудио, DOCX, XLSX, PPTX) и веб-контента (YouTube видео, веб-страницы, результаты поиска) в формат Markdown.
tags:
- Media
- Productivity
- Integration
- AI
- Web Scraping
author: Community
featured: false
---

MCP сервер для преобразования различных типов файлов (PDF, изображения, аудио, DOCX, XLSX, PPTX) и веб-контента (YouTube видео, веб-страницы, результаты поиска) в формат Markdown.

## Установка

### Из исходного кода

```bash
# Clone this repository
pnpm install
# Note: this will also install `uv` and related Python dependencies
pnpm run build
pnpm start
```

## Конфигурация

### Десктопное приложение

```json
{
  "mcpServers": {
    "markdownify": {
      "command": "node",
      "args": [
        "{ABSOLUTE PATH TO FILE HERE}/dist/index.js"
      ],
      "env": {
        // By default, the server will use the default install location of `uv`
        "UV_PATH": "/path/to/uv"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `youtube-to-markdown` | Преобразование YouTube видео в Markdown |
| `pdf-to-markdown` | Преобразование PDF файлов в Markdown |
| `bing-search-to-markdown` | Преобразование результатов поиска Bing в Markdown |
| `webpage-to-markdown` | Преобразование веб-страниц в Markdown |
| `image-to-markdown` | Преобразование изображений в Markdown с метаданными |
| `audio-to-markdown` | Преобразование аудио файлов в Markdown с транскрипцией |
| `docx-to-markdown` | Преобразование DOCX файлов в Markdown |
| `xlsx-to-markdown` | Преобразование XLSX файлов в Markdown |
| `pptx-to-markdown` | Преобразование PPTX файлов в Markdown |
| `get-markdown-file` | Получение существующего Markdown файла. Расширение файла должно заканчиваться на: *.md, *.markdown |

## Возможности

- Преобразование множества типов файлов в Markdown: PDF, изображения, аудио (с транскрипцией), DOCX, XLSX, PPTX
- Преобразование веб-контента в Markdown: транскрипты YouTube видео, результаты поиска Bing, обычные веб-страницы
- Получение существующих Markdown файлов

## Переменные окружения

### Опциональные
- `UV_PATH` - Путь к установке uv (по умолчанию используется стандартное расположение)
- `MD_SHARE_DIR` - Ограничение директории, из которой можно получать markdown файлы

## Ресурсы

- [GitHub Repository](https://github.com/zcaceres/mcp-markdownify-server)

## Примечания

В настоящее время ищем помощь с поддержкой Windows - есть готовые PR, но нужно тестирование. Использует TypeScript с Python зависимостями, установленными через uv. Доступен режим разработки с `pnpm run dev`.