---
title: Reaper MCP сервер
description: MCP сервер, который подключает проекты Reaper Digital Audio Workstation к MCP клиентам, позволяя пользователям задавать вопросы о данных и структуре их проектов Reaper.
tags:
- Media
- Productivity
- Integration
- Code
author: dschuler36
featured: false
---

MCP сервер, который подключает проекты Reaper Digital Audio Workstation к MCP клиентам, позволяя пользователям задавать вопросы о данных и структуре их проектов Reaper.

## Установка

### Из исходного кода

```bash
uv venv
source .venv/bin/activate

uv pip install .
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `find_reaper_projects` | Находит все проекты Reaper в директории, указанной в конфигурации |
| `parse_reaper_project` | Парсит проект Reaper и возвращает JSON объект |

## Возможности

- Поиск всех проектов Reaper в указанной директории
- Парсинг файлов проектов Reaper в структурированные JSON данные
- Возможность задавать вопросы на естественном языке о содержимом проектов Reaper
- Просмотр сырых данных проекта через раскрывающиеся блоки инструментов

## Примеры использования

```
Задавайте вопросы о ваших проектах Reaper (всегда указывайте имя конкретного проекта Reaper, о котором спрашиваете)
```

## Ресурсы

- [GitHub Repository](https://github.com/dschuler36/reaper-mcp-server)

## Примечания

Конфигурация требует обновления путей для установки uv, директории проектов Reaper и директории сервера в setup/claude_desktop_config.json. Сервер работает, используя find_reaper_projects для поиска проектов и parse_reaper_project для извлечения данных. Все структуры парсенных данных определены в src/domains/reaper_dataclasses.py.