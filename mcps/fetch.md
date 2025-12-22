---
title: Fetch MCP сервер
description: Сервер для загрузки веб-контента в различных форматах, включая HTML,
  JSON, обычный текст и Markdown с поддержкой пользовательских заголовков и пагинации.
tags:
- Web Scraping
- API
- Integration
- Productivity
author: Community
featured: false
---

Сервер для загрузки веб-контента в различных форматах, включая HTML, JSON, обычный текст и Markdown с поддержкой пользовательских заголовков и пагинации.

## Установка

### NPX

```bash
npx mcp-fetch-server
```

### Из исходного кода

```bash
git clone https://github.com/zcaceres/fetch-mcp
npm install
npm run build
npm start
```

## Конфигурация

### Десктопное приложение

```json
{
  "mcpServers": {
    "fetch": {
      "command": "npx",
      "args": [
        "mcp-fetch-server"
      ], 
      "env": {
        "DEFAULT_LIMIT": "50000"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `fetch_html` | Загружает веб-сайт и возвращает контент в формате HTML |
| `fetch_json` | Загружает JSON файл по URL |
| `fetch_txt` | Загружает веб-сайт и возвращает контент в виде обычного текста (без HTML) |
| `fetch_markdown` | Загружает веб-сайт и возвращает контент в формате Markdown |

## Возможности

- Загружает веб-контент с использованием современного fetch API
- Поддерживает пользовательские заголовки для запросов
- Предоставляет контент в нескольких форматах: HTML, JSON, обычный текст и Markdown
- Использует JSDOM для парсинга HTML и извлечения текста
- Использует TurndownService для конвертации HTML в Markdown
- Поддерживает пагинацию с параметрами max_length и start_index

## Переменные окружения

### Опциональные
- `DEFAULT_LIMIT` - Устанавливает лимит размера по умолчанию для загрузки (0 = без лимита)

## Ресурсы

- [GitHub Repository](https://github.com/zcaceres/fetch-mcp)

## Примечания

Доступен в NPM как mcp-fetch-server. Все инструменты загрузки поддерживают опциональные пользовательские заголовки, max_length (по умолчанию 5000) и параметры start_index для пагинированного получения контента.