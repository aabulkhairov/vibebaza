---
title: medRxiv MCP сервер
description: MCP сервер, который создает мост между AI-помощниками и репозиторием препринтов medRxiv, обеспечивая поиск и доступ к научным статьям по медицине через Model Context Protocol.
tags:
- Search
- AI
- Web Scraping
- Database
- Analytics
author: JackKuo666
featured: false
---

MCP сервер, который создает мост между AI-помощниками и репозиторием препринтов medRxiv, обеспечивая поиск и доступ к научным статьям по медицине через Model Context Protocol.

## Установка

### Smithery - Claude

```bash
npx -y @smithery/cli@latest install @JackKuo666/medrxiv-mcp-server --client claude --config "{}"
```

### Smithery - Cursor

```bash
npx -y @smithery/cli@latest run @JackKuo666/medrxiv-mcp-server --client cursor --config "{}"
```

### Smithery - Windsurf

```bash
npx -y @smithery/cli@latest install @JackKuo666/medrxiv-mcp-server --client windsurf --config "{}"
```

### Smithery - CLine

```bash
npx -y @smithery/cli@latest install @JackKuo666/medrxiv-mcp-server --client cline --config "{}"
```

### UV Tool Install

```bash
uv tool install medRxiv-mcp-server
```

## Конфигурация

### Claude Desktop (Mac OS)

```json
{
  "mcpServers": {
    "medrxiv": {
      "command": "python",
      "args": ["-m", "medrxiv-mcp-server"]
      }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "medrxiv": {
      "command": "C:\\Users\\YOUR_USERNAME\\AppData\\Local\\Programs\\Python\\Python311\\python.exe",
      "args": [
        "-m",
        "medrxiv-mcp-server"
      ]
    }
  }
}
```

### Cline

```json
{
  "mcpServers": {
    "medrxiv": {
      "command": "bash",
      "args": [
        "-c",
        "source /home/YOUR/PATH/mcp-server-medRxiv/.venv/bin/activate && python /home/YOUR/PATH/mcp-server-medRxiv/medrxiv_server.py"
      ],
      "env": {},
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_medrxiv_key_words` | Поиск статей в medRxiv по ключевым словам с опциональным ограничением количества результатов |
| `search_medrxiv_advanced` | Расширенный поиск статей в medRxiv с множественными параметрами поиска, включая авторов... |
| `get_medrxiv_metadata` | Получение метаданных статьи medRxiv по её DOI |

## Возможности

- Поиск статей: Поиск статей medRxiv с пользовательскими поисковыми запросами или расширенными параметрами поиска
- Эффективное получение данных: Быстрый доступ к метаданным статей
- Доступ к метаданным: Получение детальных метаданных для конкретных статей по DOI
- Поддержка исследований: Содействие исследованиям и анализу в области медицинских наук
- Доступ к статьям: Скачивание и чтение содержимого статей
- Список статей: Просмотр всех скачанных статей
- Локальное хранение: Статьи сохраняются локально для более быстрого доступа
- Исследовательские промпты: Набор специализированных промптов для анализа статей

## Примеры использования

```
Можешь найти в medRxiv недавние статьи о геномике?
```

```
Можешь показать мне детали статьи 10.1101/003541?
```

```
Найди статьи об эффективности вакцин против COVID-19
```

```
Найди статьи автора MacLachlan за 2020-2023 годы
```

## Ресурсы

- [GitHub Repository](https://github.com/JackKuo666/medRxiv-MCP-Server)

## Примечания

Этот инструмент предназначен только для исследовательских целей. Пожалуйста, соблюдайте условия использования medRxiv и используйте этот инструмент ответственно. Проект вдохновлен и построен на основе проекта arxiv-mcp-server. Зависимости включают Python 3.10+, FastMCP, requests и beautifulsoup4.