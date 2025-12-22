---
title: Defuddle Fetch MCP сервер
description: Сервер Model Context Protocol, который обеспечивает расширенные возможности загрузки веб-контента с использованием библиотеки Defuddle, автоматически очищая HTML и конвертируя его в читаемый markdown с лучшими результатами, чем у стандартных конвертеров.
tags:
- Web Scraping
- AI
- Integration
- API
- Productivity
author: domdomegg
featured: false
---

Сервер Model Context Protocol, который обеспечивает расширенные возможности загрузки веб-контента с использованием библиотеки Defuddle, автоматически очищая HTML и конвертируя его в читаемый markdown с лучшими результатами, чем у стандартных конвертеров.

## Установка

### NPX

```bash
npx -y defuddle-fetch-mcp-server
```

### Из исходников

```bash
git clone repository
npm install
npm run build
node /path/to/clone/defuddle-fetch-mcp-server/dist/index.js
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "defuddle-fetch": {
      "command": "npx",
      "args": [
        "-y",
        "defuddle-fetch-mcp-server"
      ]
    }
  }
}
```

### Claude Desktop (из исходников)

```json
{
  "mcpServers": {
    "defuddle-fetch": {
      "command": "node",
      "args": [
        "/path/to/clone/defuddle-fetch-mcp-server/dist/index.js"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `fetch` | Загружает URL из интернета и извлекает его содержимое как чистый markdown-текст с использованием Defuddle ... |

## Возможности

- Улучшенное извлечение контента с помощью Defuddle для удаления веб-страничного мусора и извлечения основного контента с сохранением заголовка страницы и ключевых метаданных
- Гибкий вывод с поддержкой как markdown, так и raw HTML
- Чтение по частям с пагинацией через параметры start_index и max_length
- Извлечение богатых метаданных включая заголовок, автора, дату публикации, количество слов, домен и время обработки
- Прямая замена для стандартного fetch MCP сервера с превосходными результатами для современных веб-страниц

## Примеры использования

```
Fetch a URL and extract its contents as clean, markdown text
```

## Ресурсы

- [GitHub Repository](https://github.com/domdomegg/defuddle-fetch-mcp-server)

## Примечания

Этот сервер разработан как прямая замена стандартному fetch MCP серверу, который использует Readability, обеспечивая лучшие результаты особенно для современных веб-страниц и GitHub контента. Версии следуют семантическому версионированию, а релизы автоматизированы через GitHub Actions.