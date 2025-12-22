---
title: arXiv API MCP сервер
description: MCP сервер, который позволяет взаимодействовать с arXiv API на естественном языке для поиска, получения метаданных и скачивания научных статей.
tags:
- API
- Search
- AI
- Database
- Productivity
author: prashalruchiranga
featured: false
---

MCP сервер, который позволяет взаимодействовать с arXiv API на естественном языке для поиска, получения метаданных и скачивания научных статей.

## Установка

### Из исходников (MacOS)

```bash
git clone https://github.com/prashalruchiranga/arxiv-mcp-server.git
cd arxiv-mcp-server
brew install uv
uv venv --python=python3.13
source .venv/bin/activate
uv sync
```

### Из исходников (Windows)

```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
git clone https://github.com/prashalruchiranga/arxiv-mcp-server.git
cd arxiv-mcp-server
uv venv --python=python3.13
source .venv\Scripts\activate
uv sync
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "arxiv-server": {
      "command": "uv",
      "args": [
        "--directory",
        "/ABSOLUTE/PATH/TO/PARENT/FOLDER/arxiv-mcp-server/src/arxiv_server",
        "run",
        "server.py"
      ],
      "env": {
        "DOWNLOAD_PATH": "/ABSOLUTE/PATH/TO/DOWNLOADS/FOLDER"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_article_url` | Получение URL статьи, размещенной на arXiv.org, по её названию |
| `download_article` | Скачивание статьи с arXiv.org в формате PDF |
| `load_article_to_context` | Загрузка статьи с arXiv.org в контекст языковой модели |
| `get_details` | Получение метаданных статьи с arXiv.org по её названию |
| `search_arxiv` | Выполнение поискового запроса через arXiv API с заданными параметрами и получение подходящих статей |

## Возможности

- Получение метаданных о научных статьях, размещенных на arXiv.org
- Скачивание статей в формате PDF на локальную машину
- Поиск по базе данных arXiv по определенному запросу
- Получение статей и загрузка их в контекст большой языковой модели (LLM)

## Переменные окружения

### Обязательные
- `DOWNLOAD_PATH` - Абсолютный путь к папке загрузок, где будут сохраняться PDF файлы

## Примеры использования

```
Can you get the details of 'Reasoning to Learn from Latent Thoughts' paper?
```

```
Get the papers authored or co-authored by Yann Lecun on convolutional neural networks
```

```
Download the attention is all you need paper
```

```
Can you get the papers by Andrew NG which have 'convolutional neural networks' in title?
```

```
Can you display the paper?
```

## Ресурсы

- [GitHub Repository](https://github.com/prashalruchiranga/arxiv-mcp-server)

## Примечания

Требует Python 3.13+ и менеджер пакетов uv. В конфигурации может потребоваться полный путь к исполняемому файлу uv (проверьте с помощью 'which uv' на MacOS или 'where uv' на Windows).