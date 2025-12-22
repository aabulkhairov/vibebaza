---
title: Pandoc MCP сервер
description: MCP сервер для конвертации форматов документов с использованием Pandoc, поддерживающий преобразование между Markdown, HTML, PDF, DOCX, LaTeX, EPUB и другими форматами с сохранением форматирования и структуры.
tags:
- Productivity
- Media
- API
- Code
author: vivekVells
featured: true
---

MCP сервер для конвертации форматов документов с использованием Pandoc, поддерживающий преобразование между Markdown, HTML, PDF, DOCX, LaTeX, EPUB и другими форматами с сохранением форматирования и структуры.

## Установка

### Менеджер пакетов UV

```bash
uvx mcp-pandoc
```

### Из исходников (для разработки)

```bash
uv --directory <DIRECTORY>/mcp-pandoc run mcp-pandoc
```

## Конфигурация

### Claude Desktop (опубликованная версия)

```json
{
  "mcpServers": {
    "mcp-pandoc": {
      "command": "uvx",
      "args": ["mcp-pandoc"]
    }
  }
}
```

### Claude Desktop (версия для разработки)

```json
{
  "mcpServers": {
    "mcp-pandoc": {
      "command": "uv",
      "args": [
        "--directory",
        "<DIRECTORY>/mcp-pandoc",
        "run",
        "mcp-pandoc"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `convert-contents` | Преобразует контент между поддерживаемыми форматами с опциями для входных/выходных файлов, эталонных документов... |

## Возможности

- Двустороннее преобразование между 10+ форматами документов (Markdown, HTML, PDF, DOCX, RST, LaTeX, EPUB, TXT, IPYNB, ODT)
- Поддержка эталонных документов для сохранения единообразного стиля в DOCX файлах
- YAML файлы по умолчанию для переиспользуемых шаблонов конвертации
- Пользовательские фильтры Pandoc для расширенной обработки
- Опции конвертации на основе файлов и контента
- Продвинутое сохранение форматирования между форматами

## Примеры использования

```
Convert this text to PDF and save as /path/to/document.pdf
```

```
Convert /path/to/input.md to PDF and save as /path/to/output.pdf
```

```
Convert input.md to DOCX using template.docx as reference and save as output.docx
```

```
Convert docs.md to HTML with filters ['/path/to/mermaid-filter.py'] and save as docs.html
```

```
Convert paper.md to PDF using defaults academic-paper.yaml and save as paper.pdf
```

## Ресурсы

- [GitHub Repository](https://github.com/vivekVells/mcp-pandoc)

## Примечания

Требует установки pandoc (brew install pandoc). Для конвертации в PDF необходима установка TeX Live. Для продвинутых форматов (PDF, DOCX, RST, LaTeX, EPUB) требуются полные пути к файлам с именем файла и расширением. В настоящее время находится в ранней стадии разработки, поддержка PDF активно дорабатывается.