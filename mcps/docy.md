---
title: Docy MCP сервер
description: MCP сервер, который предоставляет AI-ассистентам прямой доступ к технической документации с сайтов вроде React, Python и crawl4ai через интеллектуальный веб-скрапинг и кеширование.
tags:
- Web Scraping
- AI
- Productivity
- API
- Integration
author: oborchers
featured: false
---

MCP сервер, который предоставляет AI-ассистентам прямой доступ к технической документации с сайтов вроде React, Python и crawl4ai через интеллектуальный веб-скрапинг и кеширование.

## Установка

### uvx (рекомендуется)

```bash
uvx mcp-server-docy
```

### pip

```bash
pip install mcp-server-docy
DOCY_DOCUMENTATION_URLS="https://docs.crawl4ai.com/,https://react.dev/" python -m mcp_server_docy
```

### Docker

```bash
docker pull oborchers/mcp-server-docy:latest
docker run -i --rm -e DOCY_DOCUMENTATION_URLS="https://docs.crawl4ai.com/,https://react.dev/" oborchers/mcp-server-docy
```

## Конфигурация

### Claude Desktop - uvx

```json
"mcpServers": {
  "docy": {
    "command": "uvx",
    "args": ["mcp-server-docy"],
    "env": {
      "DOCY_DOCUMENTATION_URLS": "https://docs.crawl4ai.com/,https://react.dev/"
    }
  }
}
```

### Claude Desktop - Docker

```json
"mcpServers": {
  "docy": {
    "command": "docker",
    "args": ["run", "-i", "--rm", "oborchers/mcp-server-docy:latest"],
    "env": {
      "DOCY_DOCUMENTATION_URLS": "https://docs.crawl4ai.com/,https://react.dev/"
    }
  }
}
```

### VS Code - uvx

```json
{
  "mcp": {
    "servers": {
      "docy": {
        "command": "uvx",
        "args": ["mcp-server-docy"],
        "env": {
          "DOCY_DOCUMENTATION_URLS": "https://docs.crawl4ai.com/,https://react.dev/"
        }
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_documentation_sources_tool` | Список всех доступных источников документации |
| `fetch_documentation_page` | Получение содержимого страницы документации по URL в формате markdown |
| `fetch_document_links` | Получение всех ссылок со страницы документации |

## Возможности

- Мгновенный доступ к документации - прямой доступ к документации React, Python, crawl4ai и любых других технологий
- Поддержка горячей перезагрузки - добавление новых источников документации на лету без перезапуска через файл .docy.urls
- Умное кеширование - снижает задержки и внешние запросы, сохраняя актуальность контента
- Самостоятельное хостинг-управление - держите доступ к документации в пределах своего периметра безопасности
- Бесшовная интеграция с MCP - работает с Claude, VS Code и другими инструментами с поддержкой MCP
- Несколько транспортных протоколов - поддерживает протоколы stdio и SSE (Server-Sent Events)
- Постоянное дисковое кеширование - кеш сохраняется после перезапуска сервера для лучшей производительности

## Переменные окружения

### Опциональные
- `DOCY_DOCUMENTATION_URLS` - разделенный запятыми список URL-адресов сайтов документации для включения
- `DOCY_DOCUMENTATION_URLS_FILE` - путь к файлу, содержащему URL документации, по одному на строку (по умолчанию: ".docy.urls")
- `DOCY_CACHE_TTL` - время жизни кеша в секундах (по умолчанию: 432000)
- `DOCY_CACHE_DIRECTORY` - путь к директории кеша (по умолчанию: ".docy.cache")
- `DOCY_USER_AGENT` - пользовательская строка User-Agent для HTTP-запросов
- `DOCY_DEBUG` - включить отладочное логирование ("true", "1", "yes", или "y")
- `DOCY_SKIP_CRAWL4AI_SETUP` - пропустить выполнение команды crawl4ai-setup при запуске ("true", "1", "yes", или "y")
- `DOCY_TRANSPORT` - транспортный протокол для использования (опции: "sse" или "stdio", по умолчанию: "stdio")

## Примеры использования

```
Правильно ли мы реализуем результаты скрапинга Crawl4Ai? Давайте проверим документацию.
```

```
Что говорит документация об использовании mcp.tool? Покажи мне примеры из документации.
```

```
Как нам следует структурировать данные согласно документации React? Какие есть лучшие практики?
```

```
Пожалуйста, используй Docy для поиска...
```

## Ресурсы

- [GitHub Repository](https://github.com/oborchers/mcp-server-docy)

## Примечания

Claude может по умолчанию использовать встроенный WebFetchTool вместо Docy. Чтобы явно запросить функциональность Docy, используйте такую фразу как 'Пожалуйста, используй Docy для поиска...'. Сервер поддерживает горячую перезагрузку файлов конфигурации URL, позволяя добавлять/изменять источники документации без перезапуска. Глобальная настройка сервера доступна для команд через server/README.md для запуска постоянного SSE сервера.