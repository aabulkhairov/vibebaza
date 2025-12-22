---
title: bioRxiv MCP сервер
description: Обеспечивает связь между AI-ассистентами и репозиторием препринтов bioRxiv через Model Context Protocol, позволяя AI-моделям искать биологические препринты и программно получать доступ к их метаданным.
tags:
- Search
- Database
- AI
- Web Scraping
- API
author: JackKuo666
featured: false
---

Обеспечивает связь между AI-ассистентами и репозиторием препринтов bioRxiv через Model Context Protocol, позволяя AI-моделям искать биологические препринты и программно получать доступ к их метаданным.

## Установка

### Из исходного кода

```bash
git clone https://github.com/JackKuo666/bioRxiv-MCP-Server.git
cd bioRxiv-MCP-Server
pip install -r requirements.txt
```

### Smithery (Claude)

```bash
npx -y @smithery/cli@latest install @JackKuo666/biorxiv-mcp-server --client claude --config "{}"
```

### Smithery (Cursor)

```bash
npx -y @smithery/cli@latest run @JackKuo666/biorxiv-mcp-server --client cursor --config "{}"
```

### Smithery (Windsurf)

```bash
npx -y @smithery/cli@latest install @JackKuo666/biorxiv-mcp-server --client windsurf --config "{}"
```

### Smithery (CLine)

```bash
npx -y @smithery/cli@latest install @JackKuo666/biorxiv-mcp-server --client cline --config "{}"
```

## Конфигурация

### Claude Desktop (Mac OS)

```json
{
  "mcpServers": {
    "biorxiv": {
      "command": "python",
      "args": ["-m", "biorxiv-mcp-server"]
      }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "biorxiv": {
      "command": "C:\\Users\\YOUR_USERNAME\\AppData\\Local\\Programs\\Python\\Python311\\python.exe",
      "args": [
        "-m",
        "biorxiv-mcp-server"
      ]
    }
  }
}
```

### Cline

```json
{
  "mcpServers": {
    "biorxiv": {
      "command": "bash",
      "args": [
        "-c",
        "source /home/YOUR/PATH/mcp-server-bioRxiv/.venv/bin/activate && python /home/YOUR/PATH/mcp-server-bioRxiv/biorxiv_server.py"
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
|------------|----------|
| `search_biorxiv_key_words` | Поиск статей на bioRxiv по ключевым словам |
| `search_biorxiv_advanced` | Расширенный поиск статей на bioRxiv с множественными параметрами |
| `get_biorxiv_metadata` | Получение метаданных для статьи bioRxiv по её DOI |

## Возможности

- Поиск статей: Запросы к статьям bioRxiv по ключевым словам или расширенному поиску
- Эффективное получение данных: Быстрый доступ к метаданным статей
- Доступ к метаданным: Получение детальных метаданных для конкретных статей
- Поддержка исследований: Содействие исследованиям и анализу в биологических науках
- Доступ к статьям: Скачивание и чтение содержимого статей
- Список статей: Просмотр всех скачанных статей
- Локальное хранение: Статьи сохраняются локально для более быстрого доступа
- Исследовательские промпты: Набор специализированных промптов для анализа статей

## Примеры использования

```
Can you search bioRxiv for recent papers about genomics?
```

```
Can you show me the metadata for the paper with DOI 10.1101/123456?
```

## Ресурсы

- [GitHub Repository](https://github.com/JackKuo666/bioRxiv-MCP-Server)

## Примечания

Требует Python 3.10+ и библиотеку FastMCP. Этот инструмент предназначен только для исследовательских целей - пожалуйста, соблюдайте условия использования bioRxiv и используйте ответственно.