---
title: SearXNG Public MCP сервер
description: MCP сервер для запросов к публичным экземплярам SearXNG, который парсит HTML-контент в JSON-результат с поддержкой резервных серверов.
tags:
- Search
- Web Scraping
- API
author: pwilkin
featured: false
---

MCP сервер для запросов к публичным экземплярам SearXNG, который парсит HTML-контент в JSON-результат с поддержкой резервных серверов.

## Установка

### NPM

```bash
npm install mcp-searxng-public
```

## Конфигурация

### Cursor/Cursor-compatible

```json
{
  "SearXNGScraper": {
    "command": "npx",
    "args": ["mcp-searxng-public"],
    "capabilities": {
      "tool-calls": true
    },
    "env": {
      "SEARXNG_BASE_URL": "https://metacat.online;https://nyc1.sx.ggtyler.dev;https://ooglester.com;https://search.080609.xyz;https://search.canine.tools;https://search.catboy.house;https://search.citw.lgbt;https://search.einfachzocken.eu;https://search.federicociro.com;https://search.hbubli.cc;https://search.im-in.space;https://search.indst.eu",
      "DEFAULT_LANGUAGE": "en"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search` | Выполняет поисковые запросы к публичным экземплярам SearXNG с опциональным временным диапазоном, языком и ... |

## Возможности

- Запросы к публичным экземплярам SearXNG, которые не предоставляют JSON-формат
- Парсинг HTML-результатов в структурированный JSON
- Поддержка до трех серверов SearXNG с механизмом резервного копирования
- Фильтрация по временному диапазону (день, месяц, год)
- Поддержка поиска по конкретному языку
- Детальный режим поиска, который запрашивает несколько серверов и страниц
- Дедупликация и объединение результатов

## Переменные окружения

### Обязательные
- `SEARXNG_BASE_URL` - Список URL-адресов экземпляров SearXNG, разделенных точкой с запятой, для использования в поиске

### Опциональные
- `DEFAULT_LANGUAGE` - Код языка по умолчанию для поиска (например, 'en', 'es', 'fr')

## Примеры использования

```
Search for information about a topic
```

```
Find recent articles from the past day/month/year
```

```
Search in a specific language
```

```
Perform detailed searches across multiple servers for comprehensive results
```

## Ресурсы

- [GitHub Repository](https://github.com/pwilkin/mcp-searxng-public)

## Примечания

Сервер решает проблемы других MCP серверов SearXNG, которые не работают с публичными экземплярами, за счет парсинга HTML вместо использования JSON-формата. Включает задачу 'report' для определения доступных экземпляров SearXNG. Возвращает структурированные результаты с полями URL и резюме.