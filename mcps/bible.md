---
title: Bible MCP сервер
description: MCP сервер, который предоставляет доступ к библейскому контенту через bible-api.com для больших языковых моделей, обеспечивая доступ к стихам, главам, множественным переводам и инструментам изучения Библии.
tags:
- API
- Productivity
- Database
author: Trevato
featured: false
---

MCP сервер, который предоставляет доступ к библейскому контенту через bible-api.com для больших языковых моделей, обеспечивая доступ к стихам, главам, множественным переводам и инструментам изучения Библии.

## Установка

### Из PyPI

```bash
pip install bible-mcp
```

### Из исходников

```bash
git clone https://github.com/trevato/bible-mcp.git
cd bible-mcp
pip install -e .
```

### Инструменты разработки MCP

```bash
mcp dev bible_server.py
```

### Установка для Claude Desktop

```bash
mcp install bible_server.py
```

### Прямое выполнение

```bash
python -m bible_server
```

## Конфигурация

### Claude Desktop

```json
"Bible MCP": {
    "command": "uvx",
    "args": [
    "bible-mcp"
    ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_verse_by_reference` | Получает библейские стихи по ссылке (например, 'John 3:16', 'Matthew 5:1-10') с опциональным переводом... |
| `get_random_verse_tool` | Получает случайный стих с опциональной фильтрацией по завету (OT/NT) и выбором перевода |
| `list_available_translations` | Возвращает отформатированный список всех доступных переводов Библии |

## Возможности

- Доступ к библейским стихам и главам как к ресурсам
- Инструменты для получения стихов по ссылке и получения случайных стихов
- Поддержка множественных переводов (KJV, Web, ASV, BBE и другие)
- Шаблоны промптов для изучения Библии
- Настоящая генерация случайных стихов из любой книги Библии
- Фильтрация по завету (OT/NT) для случайных стихов
- Комплексная обработка ошибок
- URI ресурсов для глав, стихов и случайных стихов

## Примеры использования

```
Get John 3:16 from the King James Version
```

```
Find a random verse from the New Testament
```

```
Analyze the meaning of Psalm 23:1
```

```
Find verses about love
```

```
Get the entire third chapter of John from the World English Bible
```

## Ресурсы

- [GitHub Repository](https://github.com/trevato/bible-mcp)

## Примечания

Требует Python 3.10+. Использует сервис bible-api.com для библейского контента. Поддерживает URI ресурсов в формате bible://{translation}/{book}/{chapter} или bible://{translation}/{book}/{chapter}/{verse}. Включает шаблоны промптов для анализа стихов и поиска стихов по темам.