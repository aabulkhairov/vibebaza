---
title: Substack/Medium MCP сервер
description: MCP сервер, который подключает Claude к вашим публикациям на Substack и Medium,
  обеспечивая семантический поиск и анализ вашего опубликованного контента через RSS-каналы
  и эмбеддинги.
tags:
- Web Scraping
- Search
- AI
- Analytics
- Productivity
author: Community
featured: false
---

MCP сервер, который подключает Claude к вашим публикациям на Substack и Medium, обеспечивая семантический поиск и анализ вашего опубликованного контента через RSS-каналы и эмбеддинги.

## Установка

### Из исходников с uv

```bash
git clone https://github.com/yourusername/writer-context-tool.git
cd writer-context-tool
curl -LsSf https://astral.sh/uv/install.sh | sh
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
```

### Из исходников с pip

```bash
git clone https://github.com/yourusername/writer-context-tool.git
cd writer-context-tool
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "writer-tool": {
      "command": "${UV_PATH}",
      "args": [
        "--directory",
        "$(pwd)",
        "run",
        "writer_tool.py"
      ]
    }
  }
}
```

### Конфигурация платформ

```json
{
  "platforms": [
    {
      "type": "substack",
      "url": "https://yourusername.substack.com",
      "name": "My Substack Blog"
    },
    {
      "type": "medium",
      "url": "https://medium.com/@yourusername",
      "name": "My Medium Blog"
    }
  ],
  "max_posts": 100,
  "cache_duration_minutes": 10080,
  "similar_posts_count": 10
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_writing` | Инструмент семантического поиска, который находит наиболее релевантные эссе с использованием эмбеддингов |
| `refresh_content` | Обновляет и перекеширует ваш контент со всех настроенных платформ |

## Возможности

- Извлекает и постоянно кеширует ваши блог-посты с Substack и Medium
- Использует эмбеддинги для поиска наиболее релевантных эссе на основе ваших запросов
- Делает отдельные эссе доступными как отдельные ресурсы для Claude
- Выполняет семантический поиск по вашим текстам
- Предварительно загружает весь контент и генерирует эмбеддинги при запуске

## Примеры использования

```
Find essays where I discuss [specific topic]
```

```
What have I written about [subject]?
```

```
Show me the full text of [essay title]
```

```
Refresh my writing content
```

## Ресурсы

- [GitHub Repository](https://github.com/jonathan-politzki/mcp-writer-substack)

## Примечания

Требует Python 3.10 или выше и аккаунт на Substack или Medium с опубликованным контентом. Инструмент подключается через RSS-каналы и использует постоянное дисковое кеширование с эмбеддингами для семантического поиска.