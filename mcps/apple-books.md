---
title: Apple Books MCP сервер
description: MCP сервер для Apple Books, который позволяет взаимодействовать с вашей библиотекой, управлять коллекцией книг, выделениями, заметками и аннотациями.
tags:
- Media
- Productivity
- Analytics
- Search
- Integration
author: Community
featured: false
---

MCP сервер для Apple Books, который позволяет взаимодействовать с вашей библиотекой, управлять коллекцией книг, выделениями, заметками и аннотациями.

## Установка

### uvx (рекомендуется)

```bash
brew install uv  # for macos
uvx apple-books-mcp
```

### pip

```bash
pip install apple-books-mcp
python -m apple_books_mcp
```

## Конфигурация

### Claude Desktop (uvx)

```json
{
    "mcpServers": {
        "apple-books-mcp": {
            "command": "uvx",
            "args": [ "apple-books-mcp@latest" ]
        }
    }
}
```

### Claude Desktop (python)

```json
{
    "mcpServers": {
        "apple-books-mcp": {
            "command": "python",
            "args": ["-m", "apple_books_mcp"]
        }
    }
}
```

### Отладка с Claude Desktop

```json
{
    "mcpServers": {
        "apple-books-mcp": {
            "command": "uv",
            "args": [
                "--directory",
                "/path/to/apple-books-mcp/",
                "run",
                "apple_books_mcp",
                "-v"
            ]
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_collections` | Список всех коллекций |
| `get_collection_books` | Получить все книги в коллекции |
| `describe_collection` | Получить детали коллекции |
| `list_all_books` | Список всех книг |
| `get_book_annotations` | Получить все аннотации для книги |
| `describe_book` | Получить детали конкретной книги |
| `list_all_annotations` | Список всех аннотаций |
| `get_highlights_by_color` | Получить все выделения по цвету |
| `search_highlighted_text` | Поиск выделений по выделенному тексту |
| `search_notes` | Поиск заметок |
| `full_text_search` | Поиск аннотаций, содержащих заданный текст |
| `recent_annotations` | Получить 10 самых последних аннотаций |
| `describe_annotation` | Получить детали аннотации |

## Возможности

- Резюмирование недавних выделений
- Организация книг в библиотеке по жанрам
- Рекомендации похожих книг на основе истории чтения
- Сравнение заметок из разных книг на одну и ту же тему
- Поиск выделений и аннотаций
- Управление коллекциями книг
- Организация выделений по цветам

## Примеры использования

```
Попросите Claude резюмировать ваши недавние выделения
```

```
Попросите Claude организовать книги в вашей библиотеке по жанрам
```

```
Попросите Claude порекомендовать похожие книги на основе вашей истории чтения
```

```
Попросите Claude сравнить заметки из разных прочитанных книг на одну и ту же тему
```

## Ресурсы

- [GitHub Repository](https://github.com/vgnshiyer/apple-books-mcp)

## Примечания

Планируемые функции включают поддержку Docker, поддержку ресурсов, возможность редактирования коллекций и выделений. Для отладки используйте инспектор с командой: npx @modelcontextprotocol/inspector uvx apple-books-mcp