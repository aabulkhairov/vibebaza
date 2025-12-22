---
title: Serper MCP сервер
description: MCP сервер, который предоставляет возможности поиска Google через Serper API, позволяя LLM искать веб-контент, изображения, видео, новости, товары и многое другое.
tags:
- Search
- Web Scraping
- API
- Integration
- AI
author: garylab
featured: false
install_command: npx -y @smithery/cli install @garylab/serper-mcp-server --client
  claude
---

MCP сервер, который предоставляет возможности поиска Google через Serper API, позволяя LLM искать веб-контент, изображения, видео, новости, товары и многое другое.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @garylab/serper-mcp-server --client claude
```

### UV (рекомендуется)

```bash
# uv загрузится автоматически через uvx
# Просто добавьте в конфиг с командой uvx
```

### Pip (проект)

```bash
# Добавьте в requirements.txt:
serper-mcp-server

pip install -r requirements.txt
```

### Pip (глобально)

```bash
pip install serper-mcp-server
# или
pip3 install serper-mcp-server
```

## Конфигурация

### Claude Desktop (UV)

```json
{
    "mcpServers": {
        "serper": {
            "command": "uvx",
            "args": ["serper-mcp-server"],
            "env": {
                "SERPER_API_KEY": "<Ваш Serper API ключ>"
            }
        }
    }
}
```

### Claude Desktop (Python)

```json
{
    "mcpServers": {
        "serper": {
            "command": "python3",
            "args": ["-m", "serper_mcp_server"],
            "env": {
                "SERPER_API_KEY": "<Ваш Serper API ключ>"
            }
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `google_search` | Выполняет стандартный веб-поиск Google |
| `google_search_images` | Поиск изображений в Google Images |
| `google_search_videos` | Поиск видео в Google |
| `google_search_places` | Поиск мест и локаций в Google |
| `google_search_maps` | Поиск в Google Maps для получения данных о местоположении |
| `google_search_reviews` | Поиск отзывов и оценок |
| `google_search_news` | Поиск новостей в Google News |
| `google_search_shopping` | Поиск товаров в Google Shopping |
| `google_search_lens` | Использует Google Lens для визуального поиска |
| `google_search_scholar` | Поиск академического контента в Google Scholar |
| `google_search_patents` | Поиск в базе данных Google Patents |
| `google_search_autocomplete` | Получает предложения поиска Google |
| `webpage_scrape` | Парсит контент с веб-страниц |

## Возможности

- Комплексный поиск Google по множеству типов контента (веб, изображения, видео, новости, покупки и др.)
- Академический поиск через Google Scholar
- Функциональность поиска в базе данных патентов
- Поиск на основе местоположения с интеграцией Maps и Places
- Возможности парсинга веб-страниц
- Предложения автодополнения поиска
- Настраиваемые параметры поиска для всех инструментов

## Переменные окружения

### Обязательные
- `SERPER_API_KEY` - API ключ для сервиса Serper для доступа к функциональности Google Search

## Ресурсы

- [GitHub Repository](https://github.com/garylab/serper-mcp-server)

## Примечания

Для отладки можно использовать MCP inspector с командой 'npx @modelcontextprotocol/inspector uvx serper-mcp-server'. Сервер распространяется под лицензией MIT и требует Python 3.11+.