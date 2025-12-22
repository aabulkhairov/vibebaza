---
title: Md2doc MCP сервер
description: Model Context Protocol (MCP) сервер, который конвертирует Markdown текст в формат DOCX, используя внешний сервис конвертации с поддержкой пользовательских шаблонов и многоязычной конвертации.
tags:
- Productivity
- Code
- API
- Media
author: Yorick-Ryu
featured: false
---

Model Context Protocol (MCP) сервер, который конвертирует Markdown текст в формат DOCX, используя внешний сервис конвертации с поддержкой пользовательских шаблонов и многоязычной конвертации.

## Установка

### UVX

```bash
uvx md2doc
```

### UVX с переменной окружения

```bash
DEEP_SHARE_API_KEY="your-api-key-here" uvx md2doc
```

## Конфигурация

### Cherry Studio

```json
{
  "mcpServers": {
    "md2doc": {
      "command": "uvx",
      "args": ["md2doc"],
      "env": {
        "DEEP_SHARE_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "md2doc": {
      "command": "uvx",
      "args": ["md2doc"],
      "env": {
        "DEEP_SHARE_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `convert_markdown_to_docx` | Конвертирует markdown текст в DOCX |
| `list_templates` | Получает доступные шаблоны по языку |

## Возможности

- Конвертация Markdown текста в формат DOCX
- Поддержка пользовательских шаблонов
- Многоязычная поддержка (английский, китайский и другие)
- Автоматическое скачивание файлов в папку Загрузки пользователя
- Управление и просмотр списка шаблонов

## Переменные окружения

### Обязательные
- `DEEP_SHARE_API_KEY` - API ключ для сервиса конвертации

## Ресурсы

- [GitHub Repository](https://github.com/Yorick-Ryu/md2doc-mcp)

## Примечания

Доступен бесплатный пробный API ключ: f4e8fe6f-e39e-486f-b7e7-e037d2ec216f. Может использоваться напрямую в Python проектах с классом ConversionAPIClient. Ссылки для покупки доступны для получения полного доступа к API.