---
title: HTML to Markdown MCP сервер
description: MCP сервер для конвертации HTML-контента в формат Markdown с использованием Turndown.js. Поддерживает загрузку веб-страниц и обработку больших объёмов контента с сохранением прямо в файлы.
tags:
- Web Scraping
- Productivity
- API
- Integration
- Code
author: Community
featured: false
install_command: claude mcp add --transport stdio html-to-markdown -- npx html-to-markdown-mcp
---

MCP сервер для конвертации HTML-контента в формат Markdown с использованием Turndown.js. Поддерживает загрузку веб-страниц и обработку больших объёмов контента с сохранением прямо в файлы.

## Установка

### NPM Global

```bash
npm install -g html-to-markdown-mcp
```

### NPX

```bash
npx html-to-markdown-mcp
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "html-to-markdown": {
      "command": "npx",
      "args": ["html-to-markdown-mcp"]
    }
  }
}
```

### Claude Desktop (Global)

```json
{
  "mcpServers": {
    "html-to-markdown": {
      "command": "html-to-markdown-mcp"
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "html-to-markdown": {
      "command": "npx",
      "args": ["html-to-markdown-mcp"]
    }
  }
}
```

### Codex

```json
[mcp_servers.html-to-markdown]
command = "npx"
args = ["-y", "html-to-markdown-mcp"]
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `html_to_markdown` | Загружает HTML по URL или конвертирует переданный HTML-контент в формат Markdown с опциями для метадан... |
| `save_markdown` | Сохраняет markdown-контент в файл на диске |

## Возможности

- Автоматическая загрузка и конвертация веб-страниц с любого URL
- Конвертация HTML в чистый, отформатированный Markdown
- Сохранение форматирования (заголовки, ссылки, блоки кода, списки, таблицы)
- Автоматическое удаление нежелательных элементов (скрипты, стили и т.д.)
- Автоматическое извлечение заголовков страниц и метаданных
- Быстрая конвертация с использованием Turndown.js
- Обработка больших страниц с автоматическим сохранением в файлы для обхода лимитов токенов
- Ограничение длины контента с поддержкой обрезки

## Примеры использования

```
Что находится на https://example.com?
```

```
Загрузи и сделай резюме этой статьи: https://...
```

```
Конвертируй эту веб-страницу в Markdown
```

```
Извлеки основной контент с этого URL
```

```
Сохрани эту веб-страницу как markdown-файл
```

## Ресурсы

- [GitHub Repository](https://github.com/levz0r/html-to-markdown-mcp)

## Примечания

Сервер автоматически активируется, когда Claude нужно загрузить веб-контент или конвертировать HTML в Markdown. Поддерживает как загрузку по URL, так и конвертацию сырого HTML. Включает подробные примеры конфигурации для нескольких MCP клиентов, включая Claude Desktop, Cursor и Codex.