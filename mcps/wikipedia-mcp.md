---
title: Wikipedia MCP сервер
description: MCP сервер, который извлекает информацию из Wikipedia для предоставления контекста большим языковым моделям, позволяя AI-ассистентам получать доступ к фактической информации из Wikipedia для обоснования своих ответов надежными источниками.
tags:
- Search
- API
- AI
- Web Scraping
- Database
author: Rudra-ravi
featured: true
install_command: npx -y @smithery/cli install @Rudra-ravi/wikipedia-mcp --client claude
---

MCP сервер, который извлекает информацию из Wikipedia для предоставления контекста большим языковым моделям, позволяя AI-ассистентам получать доступ к фактической информации из Wikipedia для обоснования своих ответов надежными источниками.

## Установка

### pipx (Рекомендуется)

```bash
pip install pipx
pipx ensurepath
pipx install wikipedia-mcp
```

### Smithery

```bash
npx -y @smithery/cli install @Rudra-ravi/wikipedia-mcp --client claude
```

### PyPI

```bash
pip install wikipedia-mcp
```

### Виртуальное окружение

```bash
python3 -m venv venv
source venv/bin/activate
pip install git+https://github.com/rudra-ravi/wikipedia-mcp.git
```

### Из исходного кода

```bash
git clone https://github.com/rudra-ravi/wikipedia-mcp.git
cd wikipedia-mcp
python3 -m venv wikipedia-mcp-env
source wikipedia-mcp-env/bin/activate
pip install -e .
```

## Конфигурация

### Claude Desktop базовая

```json
{
  "mcpServers": {
    "wikipedia": {
      "command": "wikipedia-mcp"
    }
  }
}
```

### Claude Desktop полный путь

```json
{
  "mcpServers": {
    "wikipedia": {
      "command": "/full/path/to/wikipedia-mcp"
    }
  }
}
```

### Claude Desktop мультиязычная

```json
{
  "mcpServers": {
    "wikipedia-us": {
      "command": "wikipedia-mcp",
      "args": ["--country", "US"]
    },
    "wikipedia-taiwan": {
      "command": "wikipedia-mcp", 
      "args": ["--country", "TW"]
    },
    "wikipedia-japan": {
      "command": "wikipedia-mcp",
      "args": ["--country", "Japan"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_wikipedia` | Поиск статей Wikipedia по запросу с опциональным ограничением количества результатов |
| `get_article` | Получение полного содержания статьи Wikipedia, включая текст, резюме, разделы, ссылки и категории |
| `get_summary` | Получение краткого резюме статьи Wikipedia |
| `get_sections` | Получение разделов статьи Wikipedia в структурированном списке |
| `get_links` | Получение ссылок, содержащихся в статье Wikipedia, на другие статьи |
| `get_coordinates` | Получение координат статьи Wikipedia с широтой, долготой и метаданными |
| `get_related_topics` | Получение тем, связанных со статьей Wikipedia, на основе ссылок и категорий |
| `summarize_article_for_query` | Получение резюме статьи Wikipedia, адаптированного под конкретный запрос |
| `summarize_article_section` | Получение резюме определенного раздела статьи Wikipedia |
| `extract_key_facts` | Извлечение ключевых фактов из статьи Wikipedia, опционально сфокусированных на конкретной теме |

## Возможности

- Поиск статей Wikipedia с расширенной диагностикой
- Получение полного содержания статьи со всей информацией
- Получение кратких резюме статей
- Извлечение определенных разделов из статей
- Обнаружение ссылок в статьях на связанные темы
- Поиск тем, связанных с определенными статьями
- Поддержка мультиязычности с кодами языков
- Поддержка стран/локалей с интуитивными кодами стран
- Поддержка языковых вариантов (традиционный/упрощенный китайский, сербские письменности и т.д.)
- Опциональное кеширование для улучшенной производительности

## Переменные окружения

### Опциональные
- `WIKIPEDIA_ACCESS_TOKEN` - токен персонального доступа для избежания ограничений по скорости (ошибки 403)

## Ресурсы

- [Репозиторий на GitHub](https://github.com/Rudra-ravi/wikipedia-mcp)

## Примечания

Поддерживает 140+ стран и регионов с автоматическим сопоставлением языков. Расположение файлов конфигурации: macOS: ~/Library/Application Support/Claude/claude_desktop_config.json, Windows: %APPDATA%/Claude/claude_desktop_config.json, Linux: ~/.config/Claude/claude_desktop_config.json. Используйте --list-countries для просмотра всех поддерживаемых кодов стран.