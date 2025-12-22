---
title: AWS Open Data MCP сервер
description: MCP сервер для поиска и изучения датасетов из AWS Open Data Registry с нечётким поиском и автоматическим кэшированием для быстрых запросов.
tags:
- Search
- Cloud
- Analytics
- Database
- API
author: domdomegg
featured: false
install_command: claude mcp add aws-open-data --transport http http://localhost:3000/mcp
---

MCP сервер для поиска и изучения датасетов из AWS Open Data Registry с нечётким поиском и автоматическим кэшированием для быстрых запросов.

## Установка

### Из исходников

```bash
npm install
npm start
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_datasets` | Поиск датасетов по названию, описанию или тегам с нечётким поиском. Возвращает все датасеты если не... |
| `get_dataset` | Получение детальной информации о конкретном датасете по его имени файла. |

## Возможности

- Поиск датасетов по названию, описанию или тегам с нечётким поиском
- Получение детальной информации о конкретном датасете
- Автоматическое кэширование AWS Open Data Registry для быстрых запросов

## Ресурсы

- [GitHub Repository](https://github.com/domdomegg/aws-open-data-mcp)

## Примечания

Сервер запускается на http://localhost:3000/mcp используя потоковый HTTP транспорт. Claude Code нужно перезапустить после добавления MCP. Поиск поддерживает настраиваемые уровни детализации (nameOnly, minimal, full) и ограничения результатов.