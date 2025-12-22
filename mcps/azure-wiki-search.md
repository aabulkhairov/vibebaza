---
title: Azure Wiki Search MCP сервер
description: MCP сервер, который реализует спецификацию MCP, позволяя AI агентам искать и получать контент из Azure DevOps Wiki.
tags:
- Search
- DevOps
- Cloud
- API
- Productivity
author: coder-linping
featured: false
---

MCP сервер, который реализует спецификацию MCP, позволяя AI агентам искать и получать контент из Azure DevOps Wiki.

## Установка

### Из исходного кода

```bash
git clone https://github.com/coder-linping/azure-wiki-search-server.git
cd azure-wiki-search-server

# Windows:
uv venv
.venv/Scripts/activate

# Mac/Linux:
uv venv
source .venv/bin/activate
```

## Конфигурация

### VS Code

```json
{
  "mcp": {
    "servers": {
      "edge_wiki": {
        "command": "uv",
        "args": [
            "--directory",
            "<absolute path to your cloned folder>",
            "run",
            "src/edge_wiki.py"
        ],
        "env": {
            "ORG": "Your organization，default is microsoft",
            "PROJECT": "Your project, default is Edge"
        }
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_wiki` | Поиск в Edge Wiki для нахождения связанных материалов по заданному запросу |
| `get_wiki_by_path` | Получение контента wiki по указанному пути |

## Возможности

- Поиск контента в Azure DevOps Wiki
- Получение конкретных страниц wiki по пути
- Интеграция с VS Code через GitHub Copilot

## Переменные окружения

### Опциональные
- `ORG` - Ваша организация (по умолчанию microsoft)
- `PROJECT` - Ваш проект (по умолчанию Edge)

## Ресурсы

- [GitHub Repository](https://github.com/coder-linping/azure-wiki-search-server)

## Примечания

Требует VS Code с расширениями GitHub Copilot, Python 3.10+ и менеджер пакетов uv. Конфигурацию можно добавить в пользовательские настройки VS Code (JSON) или в .vscode/mcp.json для совместного использования в рабочем пространстве.