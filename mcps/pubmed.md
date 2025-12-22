---
title: PubMed MCP сервер
description: PubMed MCP сервер обеспечивает мост между AI-ассистентами и огромным репозиторием биомедицинской литературы PubMed, позволяя AI-моделям искать научные статьи, получать доступ к их метаданным и выполнять глубокий анализ программно.
tags:
- Database
- Search
- API
- Analytics
author: Community
featured: false
---

PubMed MCP сервер обеспечивает мост между AI-ассистентами и огромным репозиторием биомедицинской литературы PubMed, позволяя AI-моделям искать научные статьи, получать доступ к их метаданным и выполнять глубокий анализ программно.

## Установка

### Smithery - Claude

```bash
npx -y @smithery/cli install @JackKuo666/pubmed-mcp-server --client claude
```

### Smithery - Cursor

```bash
npx -y @smithery/cli@latest run @JackKuo666/pubmed-mcp-server --client cursor --config "{}"
```

### Smithery - Windsurf

```bash
npx -y @smithery/cli@latest install @JackKuo666/pubmed-mcp-server --client windsurf --config "{}"
```

### Smithery - CLine

```bash
npx -y @smithery/cli@latest install @JackKuo666/pubmed-mcp-server --client cline --config "{}"
```

### Из исходников

```bash
git clone https://github.com/JackKuo666/PubMed-MCP-Server.git
cd PubMed-MCP-Server
pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop (Mac OS)

```json
{
  "mcpServers": {
    "pubmed": {
      "command": "python",
      "args": ["-m", "pubmed-mcp-server"]
      }
  }
}
```

### Claude Desktop (Windows)

```json
{
  "mcpServers": {
    "pubmed": {
      "command": "C:\\Users\\YOUR\\PATH\\miniconda3\\envs\\mcp_server\\python.exe",
      "args": [
        "D:\\code\\YOUR\\PATH\\PubMed-MCP-Server\\pubmed_server.py"
      ],
      "env": {},
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

### Cline

```json
{
  "mcpServers": {
    "pubmed": {
      "command": "bash",
      "args": [
        "-c",
        "source /home/YOUR/PATH/mcp-server-pubmed/.venv/bin/activate && python /home/YOUR/PATH/pubmed-mcp-server.py"
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
| `search_pubmed_key_words` | Поиск статей в PubMed по ключевым словам |
| `search_pubmed_advanced` | Расширенный поиск статей в PubMed с несколькими параметрами |
| `get_pubmed_article_metadata` | Получение метаданных статьи PubMed по её PMID |
| `download_pubmed_pdf` | Попытка скачивания полнотекстового PDF для статьи PubMed |
| `deep_paper_analysis` | Всестороннний анализ статьи PubMed |

## Возможности

- Поиск статей: Запросы к статьям PubMed по ключевым словам или расширенному поиску
- Эффективное получение данных: Быстрый доступ к метаданным статей
- Доступ к метаданным: Получение подробных метаданных для конкретных статей
- Поддержка исследований: Помощь в исследованиях и анализе в области биомедицинских наук
- Доступ к статьям: Попытка скачивания полнотекстового PDF-контента
- Глубокий анализ: Всесторонний анализ статей
- Исследовательские промпты: Набор специализированных промптов для анализа статей

## Примеры использования

```
Можешь найти в PubMed свежие статьи про CRISPR?
```

```
Покажи мне метаданные статьи с PMID 12345678?
```

```
Выполни глубокий анализ статьи с PMID 12345678?
```

## Ресурсы

- [GitHub Repository](https://github.com/JackKuo666/PubMed-MCP-Server)

## Примечания

Этот инструмент предназначен только для исследовательских целей. Пожалуйста, соблюдайте условия использования PubMed и используйте этот инструмент ответственно. Требует Python 3.10+ и библиотеку FastMCP.