---
title: Web Search MCP сервер
description: TypeScript MCP сервер, который предоставляет комплексные возможности веб-поиска
  через прямые соединения (API ключи не требуются) с несколькими поисковыми системами, включая
  Bing, Brave и DuckDuckGo, а также полное извлечение содержимого страниц.
tags:
- Search
- Web Scraping
- Browser
- AI
- Integration
author: Community
featured: false
---

TypeScript MCP сервер, который предоставляет комплексные возможности веб-поиска через прямые соединения (API ключи не требуются) с несколькими поисковыми системами, включая Bing, Brave и DuckDuckGo, а также полное извлечение содержимого страниц.

## Установка

### Из релиза

```bash
# Download latest release zip from GitHub
# Extract to desired location
npm install
npx playwright install
npm run build
```

### Из исходного кода

```bash
git clone https://github.com/mrkrsl/web-search-mcp.git
cd web-search-mcp
npm install
npx playwright install
npm run build
```

## Конфигурация

### Базовая конфигурация

```json
{
  "mcpServers": {
    "web-search": {
      "command": "node",
      "args": ["/path/to/extracted/web-search-mcp/dist/index.js"]
    }
  }
}
```

### С переменными окружения

```json
{
  "mcpServers": {
    "web-search": {
      "command": "node",
      "args": ["/path/to/web-search-mcp/dist/index.js"],
      "env": {
        "MAX_CONTENT_LENGTH": "10000",
        "BROWSER_HEADLESS": "true",
        "MAX_BROWSERS": "3",
        "BROWSER_FALLBACK_THRESHOLD": "3"
      }
    }
  }
}
```

### Конфигурация LibreChat

```json
mcpServers:
  web-search:
    type: stdio
    command: node
    args:
    - /app/mcp/web-search-mcp/dist/index.js
    serverInstructions: true
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `full-web-search` | Комплексный веб-поиск, который выполняет поиск по нескольким системам и извлекает полное содержимое страниц из ре... |
| `get-web-search-summaries` | Легковесный поиск, который возвращает только фрагменты результатов поиска без полного извлечения содержимого... |
| `get-single-web-page-content` | Извлекает основное содержимое с конкретной веб-страницы по URL, удаляя навигацию, рекламу и другой несодержательный контент... |

## Возможности

- Поиск по нескольким системам с приоритетом Bing > Brave > DuckDuckGo
- Полное извлечение содержимого страниц из результатов поиска
- Умная стратегия запросов с переключением между браузерами Playwright и axios запросами
- Параллельная обработка нескольких страниц одновременно
- Выделенная изоляция браузеров с автоматической очисткой
- Восстановление после ошибок HTTP/2 с автоматическим переходом на HTTP/1.1
- Валидация качества результатов поиска и проверка релевантности

## Переменные окружения

### Опциональные
- `MAX_CONTENT_LENGTH` - Максимальная длина контента в символах (по умолчанию: 500000)
- `DEFAULT_TIMEOUT` - Таймаут по умолчанию для запросов в миллисекундах (по умолчанию: 6000)
- `MAX_BROWSERS` - Максимальное количество экземпляров браузера для поддержания (по умолчанию: 3)
- `BROWSER_TYPES` - Список типов браузеров через запятую (по умолчанию: 'chromium,firefox')
- `BROWSER_FALLBACK_THRESHOLD` - Количество сбоев axios перед использованием браузера как fallback (по умолчанию: 3)
- `ENABLE_RELEVANCE_CHECKING` - Включить/выключить валидацию качества результатов поиска (по умолчанию: true)
- `RELEVANCE_THRESHOLD` - Минимальная оценка качества для результатов поиска (0.0-1.0, по умолчанию: 0.3)
- `FORCE_MULTI_ENGINE_SEARCH` - Попробовать все поисковые системы и вернуть лучшие результаты (по умолчанию: false)

## Примеры использования

```
Поиск 'TypeScript MCP server' и получение полного контента из топ-3 результатов
```

```
Получение быстрых сводок для 'latest AI developments' без полного извлечения страниц
```

```
Извлечение основного содержимого с конкретной веб-страницы по URL
```

## Ресурсы

- [GitHub Repository](https://github.com/mrkrsl/web-search-mcp)

## Примечания

Протестировано с LM Studio и LibreChat. Лучше всего работает с современными моделями типа Qwen3 и Gemma 3. Требует Node.js 18.0.0+ и npm 8.0.0+. Могут быть проблемы совместимости со старыми моделями Llama и Deepseek.