---
title: mcp-grep MCP сервер
description: Python MCP сервер, который предоставляет функциональность grep, позволяя LLM искать шаблоны в файлах с использованием системного бинарника grep через запросы на естественном языке.
tags:
- Search
- DevOps
- Code
- Productivity
- API
author: erniebrodeur
featured: false
---

Python MCP сервер, который предоставляет функциональность grep, позволяя LLM искать шаблоны в файлах с использованием системного бинарника grep через запросы на естественном языке.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @erniebrodeur/mcp-grep --client claude
```

### Ручная установка

```bash
pip install mcp-grep
```

### Разработка

```bash
git clone https://github.com/erniebrodeur/mcp-grep.git
cd mcp-grep
pip install -e ".[dev]"
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `grep` | Поиск шаблонов в файлах с использованием системного бинарника grep |

## Возможности

- Информация о системном бинарнике grep (путь, версия, поддерживаемые функции)
- Поиск шаблонов в файлах с использованием регулярных выражений
- Поиск без учета регистра
- Контекстные строки (до и после совпадений)
- Максимальное количество совпадений
- Поиск фиксированных строк (не regex)
- Рекурсивный поиск по каталогам
- Понимание запросов на естественном языке для удобного использования с LLM
- Интерактивная отладка и тестирование через MCP Inspector

## Примеры использования

```
Search for 'error' in log.txt
```

```
Find all instances of 'WARNING' regardless of case in system.log
```

```
Search for 'exception' in error.log and show 3 lines before and after each match
```

```
Find all occurrences of 'deprecated' in the src directory and its subdirectories
```

```
Search for the exact string '.*' in config.js
```

## Ресурсы

- [GitHub Repository](https://github.com/erniebrodeur/mcp-grep)

## Примечания

Сервер включает ресурс 'grep://info', который возвращает информацию о системном бинарнике grep. Также поставляется с интеграцией MCP Inspector для веб-тестирования и отладки через команду 'mcp-grep-inspector'.