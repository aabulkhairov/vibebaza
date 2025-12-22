---
title: Google Custom Search MCP сервер
description: MCP сервер, который предоставляет возможности веб-поиска с использованием Google Custom Search API и функционал извлечения контента веб-страниц.
tags:
- Search
- Web Scraping
- API
- Integration
author: adenot
featured: false
---

MCP сервер, который предоставляет возможности веб-поиска с использованием Google Custom Search API и функционал извлечения контента веб-страниц.

## Установка

### NPX через Smithery

```bash
npx -y @smithery/cli install @adenot/mcp-google-search --client claude
```

### Из исходного кода

```bash
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "google-search": {
      "command": "npx",
      "args": [
        "-y",
        "@adenot/mcp-google-search"
      ],
      "env": {
        "GOOGLE_API_KEY": "your-api-key-here",
        "GOOGLE_SEARCH_ENGINE_ID": "your-search-engine-id-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search` | Выполняет веб-поиск с помощью Google Custom Search API со структурированными результатами, включающими заголовок, ссылку... |
| `read_webpage` | Извлекает контент с любой веб-страницы, возвращая очищенный текстовый контент с заголовком страницы и URL |

## Возможности

- Поиск по всему интернету или на конкретных сайтах с использованием Google Custom Search API
- Управление количеством результатов поиска (1-10)
- Получение структурированных результатов поиска с заголовком, ссылкой и сниппетом
- Получение и парсинг контента веб-страницы с любого URL
- Извлечение заголовка страницы и основного текстового контента
- Очистка контента путем удаления скриптов и стилей
- Возврат структурированных данных с заголовком, текстом и URL

## Переменные окружения

### Обязательные
- `GOOGLE_API_KEY` - API-ключ Google Cloud с доступом к Custom Search API
- `GOOGLE_SEARCH_ENGINE_ID` - ID поисковой системы (cx) из Programmable Search Engine

## Примеры использования

```
Поиск информации в интернете с конкретными запросами
```

```
Чтение и извлечение контента с веб-страниц
```

```
Получение структурированных результатов поиска от Google
```

```
Извлечение очищенного текстового контента с любого веб-сайта
```

## Ресурсы

- [GitHub Repository](https://github.com/adenot/mcp-google-search)

## Примечания

Требует Google Cloud проект с включенным Custom Search API и настроенным биллингом. Поддерживает отладку через MCP Inspector. Конфигурационные файлы находятся в ~/Library/Application Support/Claude/claude_desktop_config.json (macOS) или %APPDATA%/Claude/claude_desktop_config.json (Windows).